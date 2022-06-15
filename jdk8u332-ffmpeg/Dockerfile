FROM zt1115798334/centos7.9.2009-jdk8u332
RUN set -eux; 	yum -y update
RUN set -eux; \
 	yum  -y install \
 	 	make \
        gcc \
        gcc-c++ \
        git ; \
    rm -rf /var/cache/yum
RUN set -eux; \
    curl -fl -o yasm-1.3.0.tar.gz https://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz \
    && tar -zxvf yasm-1.3.0.tar.gz; \
    rm -rf yasm-1.3.0.tar.gz; \
    git clone https://code.videolan.org/videolan/x264.git x264; \
    git clone https://git.ffmpeg.org/ffmpeg.git ffmpeg; \
    cd /yasm-1.3.0; \
    ./configure --prefix=/usr/local/; \
    make; \
    make install; \
    cd /x264; \
    ./configure --prefix=/usr/local/x264 --enable-shared --enable-static --disable-asm; \
    make; \
    make install; \
    cd /ffmpeg; \
    ./configure --prefix=/usr/local/ffmpeg --enable-shared --enable-yasm --enable-libx264 --enable-gpl --enable-pthreads --extra-cflags=-I/usr/local/x264/include --extra-ldflags=-L/usr/local/x264/lib; \
    make -j7; \
    make install;

