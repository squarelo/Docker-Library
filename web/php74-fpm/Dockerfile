# 使用官方php:fpm镜像作为基础镜像
FROM php:7.4.33-fpm

# 更新包管理器并安装依赖
RUN apt-get update && \
    apt-get install -y libmariadb-dev-compat libmariadb-dev libzip-dev libmagickwand-dev imagemagick

# 安装PHP扩展
RUN docker-php-ext-install mysqli pdo_mysql zip exif gd intl bcmath opcache

# 安装Imagick扩展
RUN pecl install imagick && \
    echo "extension=imagick.so" > /usr/local/etc/php/conf.d/imagick.ini

# 安装Redis扩展
RUN pecl install redis && \
    echo "extension=redis.so" > /usr/local/etc/php/conf.d/docker-php-ext-redis.ini

# 配置PHP上传文件大小和内存限制
RUN echo "upload_max_filesize=50M" > /usr/local/etc/php/conf.d/uploads.ini && \
    echo "post_max_size=50M" >> /usr/local/etc/php/conf.d/uploads.ini && \
    echo "memory_limit=256M" > /usr/local/etc/php/conf.d/memory.ini
