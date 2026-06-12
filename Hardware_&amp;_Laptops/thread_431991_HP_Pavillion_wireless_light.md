---
title: "HP Pavillion wireless light"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by biffta on 2007-05-03
Hello chaps!

Recently got my HP Pavillion dv6000 laptop all working with Feisty (had a lot of problems with X and wireless). Everything now works sweetly and I am very happy but the wireless light on my laptop is still red when it should be blue.

I basically followed the steps outlined here
[http://ubuntuforums.org/showthread.php?t=406947]("http://ubuntuforums.org/showthread.php?t=406947")

Like I said my wireless is working but am not convinced the range is as good as in Windows and wonder if this light problem is anything to do with it. :confused:

---

### Post by EXCiD3 on 2007-05-03
My lappy has much **BETTER** wireless than in winxp. The wireless light on the left of the touchpad changes for me. I had no problems with Feisty and everything i want works completely. Post more information about your laptop.

---

### Post by biffta on 2007-05-04
Here you go mate:

**Computer Spec**
Feisty(32-bit) & Vista(32-bit) dual boot
AMD Turion(tm) 64 Mobile Technology MK-36
1Gb RAM 1x100Gb HD
Broadcom Corporation - Dell Wireless 1390 WLAN Mini-PCI Card
nVidia GeForce Go 6150 256 MB
$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

---

### Post by biffta on 2007-05-08
Just to further add I downloaded my wireless driver from the dell site:
[http://tinyurl.com/2soj8b](http://tinyurl.com/2soj8b)
I unzipped it and used it with the current latest version of ndiswrapper.

I carried out a few more test over the weekend and in certain parts of my house I can get a strong wireless signal in Windows but no connectivity whatsoever in Ubuntu. :(

---

### Post by mikykim070 on 2008-05-12
I HAVE THIS EXACT SAME PROBLEM.  my light was working until i installed the newest version of ubuntu 8.4.  i don't know what happened but it really bugs me.  can anyone offer any help that might reactivate the light?

---

