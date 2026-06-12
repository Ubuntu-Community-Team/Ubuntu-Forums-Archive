---
title: "HP 5590 scanner on Gutsy"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by rotarymike on 2008-03-05
Hi everyone

Trying to install an HP5590 scanner to gutsy XUBUNTU. It IS supported by SANE, btw.

installed sane and all related packages.

sane-find-scanner finds it no problem.

```
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1705 [hp scanjet s
canner]) at libusb:001:002
```

scanimage -L does not.

I noticed that in the gutsy repository, these files (the sane HP5590 files) are installed from the libsane-dev package - any idea where that gets installed?

what do I need to do to get from point A (sane-find-scanner working) to point c (Xsane working)?

---

### Post by jcwmoore on 2008-03-05
i've had similar issues with an hp PSC 1210, i could find the scanner, could print, but could not scan, the solution was 
```
 sudo apt-get install hpoj
```

after than I was able to scan... now there is quite a difference between the PSC 1210 and the 5590, so I can't promise that it will work

---

### Post by rotarymike on 2008-03-05
tried that, but no joy.

Complete config:
Thinkpad 600
Xubuntu 7.04 all updates applied
HP Scanjet 5590 via USB.

looks like SANE version 18 is installed as latest. Sane version 19 is the one that supports my scanner.

I've tried installing the DEB from libsane_1.0.19-2_i386.deb, but I get the following error:

```

printserver@kasumi:~/Desktop$ sudo dpkg --install libsane_1.0.19-2_i386.deb
(Reading database ... 101269 files and directories currently installed.)
Preparing to replace libsane 1.0.18-3ubuntu1 (using libsane_1.0.19-2_i386.deb) .
..
Unpacking replacement libsane ...
Replacing files in old package libsane-extras ...
dpkg: dependency problems prevent configuration of libsane:
 libsane depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 libsane depends on libgphoto2-2 (>= 2.4.0); however:
  Version of libgphoto2-2 on system is 2.3.0-0ubuntu4.
 libsane depends on libgphoto2-port0 (>= 2.4.0); however:
  Version of libgphoto2-port0 on system is 2.3.0-0ubuntu4.
 libsane depends on libsane-extras (>= 1.0.19.1); however:
  Version of libsane-extras on system is 1.0.18.5.
dpkg: error processing libsane (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsane
printserver@kasumi:~/Desktop$
```

---

### Post by magicfab on 2008-04-03
Hi,

I have that scanner which I hadn't used for about 3 years (when I got rid of the last Windows  machine I had around). I was about to sell it this week and decided to plug it in 7.10 and 8.04.

Long story short it works perfectly. In 7.10 nothing (visually) happens when turning it on, I have to start xsane. In 8.04 xsane starts automatically. In both cases it's detected and working fine. 

In 7.10 Xsane is version 0.99.1., dpkg -l libsane returns 1.0.19~cvs2007.

I remember one of the differences between Xubuntu and Ubuntu (gnome) was HAL autodetection / automounting... just a possible hint...

---

### Post by Jonothewright on 2008-05-01
I have this scanner hooked up to a Hardy desktop. When I start XSANE it gives me several error messages that look like this: "Error during CMS conversion: Could not open scanner ICM profile". After displaying all of those it allows me to make preview scans but not actual scans. Does anyone have any idea how I can fix this?

---

