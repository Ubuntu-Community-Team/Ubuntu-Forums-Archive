---
title: "Scanner not detected"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by mcf1986 on 2006-04-12
I am trying to get my lexmark x1180 to work under ubuntu and i did manage to get it to print by following the how2 here (many thanks for that). Now sane says there is basic support, i downloaded via cvs the back and front ends, and installed them but it still cannot detect my scanner (usb). Any help would be great thanks!

doing lsusb gave this if it helps.
$ lsusb
Bus 001 Device 004: ID 043d:007b Lexmark International, Inc.
Bus 001 Device 003: ID 043d:007c Lexmark International, Inc.
Bus 001 Device 002: ID 043d:007a Lexmark International, Inc.
Bus 001 Device 001: ID 0000:0000

hmm. . sudo scanimage actually does power up the scanner and a whole bunch of data it dumped into the console. but Xsane doesnt recoginse the scanner..

---

### Post by mcf1986 on 2006-04-12
ok i thought maybe upgrading xsane would solve the problem although it chruned this up.

sudo dpkg -i xsane_0.99+0.991-1_i386.deb (Reading database ... 67296 files and directories currently installed.)
Preparing to replace xsane 0.99+0.991-1 (using xsane_0.99+0.991-1_i386.deb) ...
Unpacking replacement xsane ...
dpkg: dependency problems prevent configuration of xsane:
 xsane depends on xsane-common (= 0.99+0.991-1); however:
  Version of xsane-common on system is 0.97-3ubuntu2.
 xsane depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.1.
 xsane depends on libglib2.0-0 (>= 2.8.5); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 xsane depends on libpango1.0-0 (>= 1.10.2); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 xsane depends on libusb-0.1-4 (>= 2:0.1.11); however:
  Version of libusb-0.1-4 on system is 2:0.1.10a-17ubuntu1.
 xsane depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing xsane (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xsane
--------------
These are the last two packages and there seemes to be some wierd cross dependancy..!?

jean@jean:~/Desktop$ sudo dpkg -i libpango1.0-0_1.12.0-2_i386.deb
(Reading database ... 67339 files and directories currently installed.)
Preparing to replace libpango1.0-0 1.12.0-2 (using libpango1.0-0_1.12.0-2_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libpango1.0-common (>= 1.12.0-2); however:
  Package libpango1.0-common is not configured yet.
dpkg: error processing libpango1.0-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpango1.0-0

jean@jean:~/Desktop$ sudo dpkg -i libpango1.0-common_1.12.0-2_i386.deb
(Reading database ... 67339 files and directories currently installed.)
Preparing to replace libpango1.0-common 1.12.0-2 (using libpango1.0-common_1.12.0-2_i386.deb) ...
Unpacking replacement libpango1.0-common ...
dpkg: dependency problems prevent configuration of libpango1.0-common:
 libpango1.0-common depends on libpango1.0-0 (>= 1.12.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libpango1.0-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpango1.0-common
jean@jean:~/Desktop$

---

### Post by zubrug on 2006-04-13
gedit /etc/sane.d/epson.conf
Then add this to the end with-out a # in front of it. If something similar is already there then uncoment it (remove the #)
usb 0x043d 0x007b (you might have to try an a or c instead of the b. In Terminal do a   xsane

good luck

---

