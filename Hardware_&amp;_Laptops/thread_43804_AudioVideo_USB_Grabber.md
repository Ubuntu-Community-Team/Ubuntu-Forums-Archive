---
title: "Audio/Video USB Grabber"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by dominik on 2005-06-23
Hi there,

i have the GrabBee X+  USB 2.0 Audio/Video Grabber and try to get it to work to capture Videos from my Cam to PC.

There are no official Linux Drivers, but is there a way to get it to work? I tried it with "Kino" and DVGrabber but it doesnt work. 

> dominik@ubuntu:~$ dvgrab
Error: no camera exists

dominik@ubuntu:~$ 

Any ideas? 
Heres the link to to the grabber: [http://videohome.com.tw/En_ProductDesc.php?p_no=1230000001](http://videohome.com.tw/En_ProductDesc.php?p_no=1230000001)

---

### Post by Toby2 on 2007-12-21
I've got the same product/problem, and it'd be great if it could be solved.

Does anyone know how?

---

### Post by mattip on 2008-01-30
I got this working using the em28xx module in the standard kernel of Gutsy 7.10.
I needed to load some data to the dongle, I used the method described at [http://mcentral.de/wiki/index.php5/Usbreplay]("http://mcentral.de/wiki/index.php5/Usbreplay")
to record the data using usbsnoop (in windows) then replay the initialization in linux.

---

