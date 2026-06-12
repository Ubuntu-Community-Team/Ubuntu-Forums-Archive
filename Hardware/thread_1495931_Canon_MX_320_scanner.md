---
title: "Canon MX 320 scanner"
date: 2010-05-28
forum: Hardware
---

### Post by polysot on 2010-05-28
Hi there!!!
I'm a new user of ubuntu (6 months) and i' ve just got a canon mx 320 multi.
Using the .deb files of canon the printer works good.
In the mean time using the .deb files for the scanner i get the message No device found.
I' ve used those : [software.canon-europe.com/products/0010697.asp  - Cached  - Similar]("http://software.canon-europe.com/products/0010697.asp%20-%20Cached%20-%20Similar")
Any help pls?
Does anyone used this scanner?

THANX in advance.

---

### Post by polysot on 2010-06-01
no idea please?

---

### Post by gcordoba on 2010-11-25
Same problem here. I navigated through the MX drivers comments on the canon places. They said that most of the drivers works well for several mx series with few exceptions like the mx320.
However I found this (which I still do not read yet):

[http://ubuntuforums.org/showthread.php?t=1528676](http://ubuntuforums.org/showthread.php?t=1528676)

---

### Post by gcordoba on 2010-11-26
Actually an special scangearmp for the mx320 is needed.  
The driver MX320 series ScanGear MP Ver. 1.30 for Linux(debian Packagearchive) can be downloaded from:

[http://support-sg.canon-asia.com/contents/SG/EN/0100186801.html](http://support-sg.canon-asia.com/contents/SG/EN/0100186801.html)

It works nice (I cannot work with the automatic sheet feeder yet) and even more, you can use the Gimp program to call scangearmp (file-->create-->ScanGear MP).

There is a driver for other MP's, which are supposed to work with other than mx320 scanners. Up to now I cannot find a driver useful to work with xsane.

---

### Post by gcordoba on 2011-04-10
for a m64 machine:

1- sudo dpkg -i --force-architecture ./scangearmp-common_1.30-1_i386.deb

2- sudo dpkg -i --force-architecture ./scangearmp-mx320series_1.30-1_i386.deb


3- download libgimp-2.0* from
[http://mirrors.kernel.org/ubuntu/poo...untu1_i386.deb](http://mirrors.kernel.org/ubuntu/poo...untu1_i386.deb)

4- unpack it by typing:
dpkg -x libgimp2.0_2.6.7-1ubuntu1_i386.deb .

5- as superuser move usr/lib/* to /usr/lib32/
sudo mv usr/lib/* /usr/lib32/

---

### Post by gcordoba on 2011-04-10
btw, finally, to scan using this tip, you ned to be a superuser:

$> sudo scangearmp

---

