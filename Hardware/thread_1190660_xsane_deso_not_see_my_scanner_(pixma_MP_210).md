---
title: "xsane deso not see my scanner (pixma MP 210)"
date: 2009-06-18
forum: Hardware
---

### Post by cdubet on 2009-06-18
I have installed the software located at
[http://sourceforge.net/projects/mp610linux/](http://sourceforge.net/projects/mp610linux/)
When I run «*make install*» I got the error
**SANE backend directory: NOT FOUND!**
SANE dll.conf: /etc/sane.d/dll.conf
Unable to find SANE backend directory and dll.conf!
Have you already installed the SANE package?

sane and xsane are installed

If I use /usr/local/bin/pixmascan I can use the scanner, but I run xsane, he cannot find the scanner
sane-find-scanner find it but not xsane …

What I have done:
1) editing /etc/sane.d/dll.conf
comment of v4l (xsane was detecting the web cam)
adding epkowa
epkowa is the epson device contained in package  libsane-extra

2) vi /etc/udev/rules.d/025_libsane-extras.rules 
adding
# Canon PIXMA
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1721", MODE="664", GROUP="scanner",* ENV{libsane_matched}="yes"

sudo udevcontrol reload_rules

3)in  /etc/sane.d/epson.conf
adding 
usb 0x04a9 0x1721

and uncomment
usb /dev/usbscanner0
usb /dev/usb/scanner0

4)
file /etc/udev/rules.d/45-libsane.rules was not existing
the try with xsane with an empty file fails 

It fails also with the line below in it
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1721", MODE="664", GROUP="scanner"

Is there somebody who has an idea why xsane does not detect my scanner ?

---

### Post by IcarusR on 2009-06-18
Is there any particular reason why you have installed this software from [http://sourceforge.net/projects/mp610linux/](http://sourceforge.net/projects/mp610linux/)
As far as I can see it does not support your pixma MP 210.

Reading in the supported devices documentation [http://www.sane-project.org/sane-mfgs.html#Z-CANON]("http://www.sane-project.org/sane-mfgs.html#Z-CANON") on the sane site it is classed as 'GOOD' using backend from here [http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/)
There are drivers on the cannon web site [http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One+Printers&series=All-in-One+Printers&model=PIXMA+MP210&menu=Download]("http://support-au.canon.com.au/EN/search?canonsearch=1&lang=EN&category=All-in-One+Printers&series=All-in-One+Printers&model=PIXMA+MP210&menu=Download")  as stated in this post on the forum [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=556980&page=2]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=556980&page=2")

A simple google search found all of this for me.

---

### Post by cdubet on 2009-06-28
Thanks for helping me :-)

at 
[http://mp610.blogspot.com/2008/02/canon-mp210-and-mp520-join-party.html](http://mp610.blogspot.com/2008/02/canon-mp210-and-mp520-join-party.html) it was stating that it works also with the pixma 210.
and it works partially as I can scan using the stand-alone program (/usr/local/bin/pixmascan)

I will try your solution as soon as I can (the problem is not on my own PC)

---

### Post by cdubet on 2009-07-15
in fact, the trick was to make a 
sudo touch /usr/lib/sane/libsane-dll.so.1

When installation with "make install" check if this file exists.
If not you get the error SANE backend directory: NOT FOUND!
If you create an empty one, it asks if you wish to overwrite it (and of course you say yes)
Then everything works :-)

---

