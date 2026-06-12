---
title: "Epson L351 scanner driver"
date: 2014-10-07
forum: Hardware
---

### Post by Pedroski55 on 2014-10-07
Could anyone please point me at the correct scanner driver for an Epson L351 All-in-one Printer Scanner. The printer is working fine, but neither Image scan for Linux nor Simple Scan can access the scanner.

I downloaded the correct .deb files from epson, but the scanner still won't do it!

Any tips out there, please??

---

### Post by Pedroski55 on 2014-10-07
I thought maybe xsane would do it, but xsane says 'the scanner is busy'.

I can get this:

pedro@pedro-school:~$ sudo scanimage -L
device `epkowa:usb:004:002' is a Epson L210/L350/L351 Series flatbed scanner
pedro@pedro-school:~$ 


If I only knew what to put in /etc/sane.d/epson2.conf maybe it would work!

---

### Post by Vladlenin5000 on 2014-10-07
You probably need the scanner part driver which is available at Epson Linux download center:

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=31834&DSCCHK=31ae2553d8c6f3ee9c7f45f621b8da16d9678ac4](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=31834&DSCCHK=31ae2553d8c6f3ee9c7f45f621b8da16d9678ac4)

---

### Post by Pedroski55 on 2014-10-07
I do not know what to do with a .dsc file. It is not a package that can be opened by software installer.

I already installed the other relevant packages, first iscan-data_1.30.0-1_all.deb then iscan_2.30.0-1~usb0.1.ltdl7_i386.deb

Any further tips please?

---

### Post by Pedroski55 on 2014-10-07
I downloaded the tar.gz file from the above link. I thought that might work. When I try to run the install I get:

root@pedro-bedro2:/home/pedro/Downloads/temp/iscan-2.30.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking C++ ABI version... 1002
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for cxxtestgen... no
checking for cxxtestgen.py... no
checking for cxxtestgen.pl... no
checking for dpkg... dpkg
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
checking for GTK... configure: error: Package requirements (gtk+) were not met:

No package 'gtk+' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@pedro-bedro2:/home/pedro/Downloads/temp/iscan-2.30.0# apt-get install gtk+
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gtk
root@pedro-bedro2:/home/pedro/Downloads/temp/iscan-2.30.0# 


What to do??

---

### Post by Pedroski55 on 2014-10-07
/etc/var/log/syslog had und Epson vendor id 04b8 five entries, and they were all associated with productid 08A1 so I put that in epkowa.conf and now it works fine, with xsane, simple scan and imagescan for Linux!

Part of epkowa.conf
# SEIKO EPSON's USB vendor ID is '0x04b8' (without quotes).  In order
# to find the USB product ID, use lsusb(1).
# A sample configuration for the Epson Perfection 1650 (Epson GT-8200),
# which has a product ID of 0x0110, would look as follows:
#
usb 0x04b8 0x08A1

For other printers printer/scanners you can try command line:

lsusb 

which should give you the vendor and product id

Put those values in the relevant /etc/sane.d/ .conf file and it should work!

---

