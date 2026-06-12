---
title: "Scanner Visioneer 7600 USB"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by hoj on 2009-01-22
Hi,

I tried to install the visioneer 7600 USB scanner on intrepid ibex (8.10), and it was recognized in the terminal, but not recognized by xsane. Can someone please help me? Thanks. I did the following:

sudo su

ln -sf bash /bin/sh

apt-get install libusb-dev

apt-get install gcc

apt-get install g++

apt-get install binutils

apt-get install build-essentials

apt-get install libtool

apt-get install lsb-rpm

apt-get upgrade

wget [ftp://ftp.sane-project.org/pub/sane/old-versions/sane-backends-1.0.18/sane-backends-1.0.18.tar.gz](ftp://ftp.sane-project.org/pub/sane/old-versions/sane-backends-1.0.18/sane-backends-1.0.18.tar.gz)

tar -xzf sane-backends-1.0.18.tar.gz

wget [http://www.codetrax.org/downloads/projects/viceo/sane-backends-1.0.18-viceo.diff.gz](http://www.codetrax.org/downloads/projects/viceo/sane-backends-1.0.18-viceo.diff.gz)

gunzip sane-backends-1.0.18-viceo.diff.gz

patch -p1 -b -d sane-backends-1.0.18/ < sane-backends-1.0.18-viceo.diff

cd sane-backends-1.0.18/

export BACKENDS=viceo

./configure –prefix=/usr –sysconfdir=/etc

make

mkdir 1_test_install

make DESTDIR=”$PWD/1_test_install” install

export MY_SANE_DIR=/home/iuvius/sane-backends-1.0.18/1_test_install

export PATH=$MY_SANE_DIR/usr/bin:$PATH

export LD_LIBRARY_PATH=$MY_SANE_DIR/usr/lib:$LD_LIBRARY_PATH

export SANE_DEBUG_DLL=128

export SANE_DEBUG_VICEO=128

cp 1_test_install/etc/sane.d/e1.ini /etc/sane.d/dll.d/

cp 1_test_install/etc/sane.d/lut.plg /etc/sane.d/dll.d/

cp 1_test_install/etc/sane.d/viceo.conf /etc/sane.d/dll.d

cp 1_test_install/usr/lib/sane/libsane-viceo.so.1.0.18 /usr/lib/sane/

ln -s -f libsane-viceo.so.1.0.18 /usr/lib/sane/libsane-viceo.so.1

echo “viceo” >> /etc/sane.d/dll.conf

echo “usb 0×04a7 0×0211&#8243; >> /etc/sane.d/viceo.conf

ldconfig

sane-find-scanner

scanimage -L

---

### Post by desertdog on 2009-08-23
You need the Viceo backend.See this link.

[http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/](http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/)

---

