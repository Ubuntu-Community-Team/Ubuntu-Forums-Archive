---
title: "Scanners"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by Lord C on 2005-03-19
I have a Colorado USB 9600 scanner (Primax).

I can find drivers for the LPT1 version of the scanner, but not the USB one.

SANE doesn't find it. :/

A [linux-usb.org quick search](http://www.qbik.ch/usb/devices/showdev.php?id=254) points me to [this guy's homepage](http://homepages.paradise.net.nz/stevenel/scanner/), who made a kernel patch for the scanner and drivers, but the patch is for kernel 2.4 aqnd we're now on like 2.6.10 ?

Thanks in advance for any help :)

---

### Post by David Haas on 2005-03-20
My limited understanding (I'm still a newbie) is that libusb has taken over the the usb driver functions from the kernal in linux 2.6. If so, then adding driver patches to 2.6 would be a conflict. See the comment for libusb in Synaptic package manager. Drivers for usb scanners are discussed at <http://www.xs4all.nl/~ljm/SANE-faq.html#84>. This page might give you more information relevant to your question. Fortunately, scanners are relatively inexpensive, so buying one compatible with Linux is another option, of course.

---

### Post by lorap on 2005-03-21
hi friend!
i've a usb-cd r/w and the device driver responsible to work with it's "sr0".
the check the right driver just plug your scanner in,then open "/dev" directory,then press turn the power on and off watching carefully what devices appear or disappear once you've the power on/off,those would be the drivers or probably driver you need.that's all :-)
have a nice day friend!
pavel

---

### Post by emperor on 2005-03-21
There is an forum post on the internet where Steve Ellis indicated that his E3 driver should work with the Colorado USB 9600

[http://www.qbik.ch/usb/devices/showdev.php?id=254]("http://www.qbik.ch/usb/devices/showdev.php?id=254")

Link to Steve's driver:
[http://homepages.paradise.net.nz/stevenel/scanner/]("http://homepages.paradise.net.nz/stevenel/scanner/")

However the patch appears to be quite old. 

I used to have a visoneer 7600 USB scanner and having to use this driver was one of the reasons I got rid of it. I now have an Epson 2400 Photo Scanner which is quite well supported on Linux and Epson even has their own Image Scanner (iscan) APP for Linux.  [http://www.epkowa.co.jp/english/linux_e/faq_scan.html](http://www.epkowa.co.jp/english/linux_e/faq_scan.html)

---

