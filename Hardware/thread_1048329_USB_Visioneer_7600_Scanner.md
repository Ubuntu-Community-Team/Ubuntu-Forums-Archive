---
title: "USB Visioneer 7600 Scanner"
date: 2009-01-23
forum: Hardware
---

### Post by hoj on 2009-01-23
Hi, I have a Visioneer 7600 USB Scanner and am trying to install & use it on ubuntu 8.10 intrepid ibex, xsane. I installed it with the method below. The computer recognize the scanner, but xsane does not recognize it. The sane website say that the scanner is supported. Could someone please help? Thanks.



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

### Post by desertdog on 2009-03-04
Your scanner was supported by the viceo backend. The original Viceo backend was a kernel module and only worked on the older 2.4 kernels. It is described at [http://viceo.orconhosting.net.nz/index.html](http://viceo.orconhosting.net.nz/index.html). 

This backend was later modified to work with libusb. It is described at [http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/](http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/). As described, it works with sane version 1.0.18. Sane is currently on version 1.0.19.

Good luck getting it working.

---

