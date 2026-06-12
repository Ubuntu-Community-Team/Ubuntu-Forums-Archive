---
title: "Epson 4490 Scanner?"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by ulugeyik on 2006-01-31
I am using Ubuntu Linux (Breezy Badger). I can not get my Epson 4490 to work.

I have tried the following:

1) Downloaded the .rpm iscan-1.18.0-1.c2.i386.rpm
file.
2) Converted into a .deb file "alien iscan-1.18.0-1.c2.i386.rpm".
3) dpkg-i iscan_1.18.0-1.c2.i386.rpm
4) At this point "sane-find-scanner" finds something : found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:004:005
5)chmod 0666 /proc/bus/usb/004/005
6) "scanimage -L " does not find anything.

7) So, I tried fixing this problem by removing iscan, doing
apt-get install libsane libsane-extras
8) Trying to reinstall iscan gave an error. So I removed libsane-extras (a conflict for the epkowa stuff?)
9) "scanimage -L" still does not work.
10) I followed someone's advice and
edited /etc/sane.d/epkowa.conf and added:
usb 0x04b8 0x0119
11) now scanimage -L says
"device `epkowa:libusb:004:005' is a Epson flatbed scanner"
12) but iscan says "could not send command to scanner, check scanner's status".
13) I tried commenting out epson on /etc/sane.d/dll.conf and putting epkowa there. same result.

Any help is greatly appreciated.

Thanks

ugdc
durduran at hotmail dot comismyemail

---

### Post by luca.mg on 2008-02-23
try [http://ubuntuforums.org/showthread.php?p=4389626#post4389626](http://ubuntuforums.org/showthread.php?p=4389626#post4389626) 

ciao luca

---

