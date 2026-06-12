---
title: "PHP ./configure paths; Ubuntu 8.04 Server"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by usingink on 2009-05-01
Hello,

I'm stuck compiling PHP 5.2.9 on Ubuntu 8.04 32b Server. ./configure seems to ignore all paths I'm providing it.

Given: a clean Ubuntu install.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-server

sudo apt-get install build-essential libtool libltdl3-dev libmcrypt-dev libxml2-dev libmysqlclient15-dev flex m4 mawk automake autoconf bison make libbz2-dev libpcre3-dev libssl-dev zlib1g-dev vim re2c libjpeg-dev libpng12-dev libgd2-noxpm-dev libxml2-dev 

wget [http://ru2.php.net/get/php-5.2.9.tar.gz/from/ru.php.net/mirror](http://ru2.php.net/get/php-5.2.9.tar.gz/from/ru.php.net/mirror)
wget [http://php-fpm.anight.org/downloads/head/php-5.2.8-fpm-0.5.10.diff.gz](http://php-fpm.anight.org/downloads/head/php-5.2.8-fpm-0.5.10.diff.gz)
tar xzvf php-5.2.9.tar.gz
gzip -cd php-5.2.8-fpm-0.5.10.diff.gz | patch -d php-5.2.9 -p1
# applying a PHP-FPM patch makes no sense

cd php-5.2.9
./configure --enable-fastcgi --enable-fpm --enable-exif --with-mcrypt --with-zlib --enable-mbstring --with-openssl=/usr/include/openssl --with-mysql --with-mysql-sock --with-gd --with-gettext --with-jpeg-dir=/usr/lib --enable-gd-native-ttf --without-sqlite --disable-pdo --disable-reflection --with-libdir=lib64 --with-postgresql

[error: Cannot find OpenSSL's libraries]


Only if I manually edit ./configure:
OPENSSL_LIBDIR=/usr/include/openssl
OPENSSL_INCDIR=/usr/include/openssl

the script goes on.

Then it hangs on libjpeg error. Again, manually editing paths in a configure script allows it to move on. Then a libpng error.

---

