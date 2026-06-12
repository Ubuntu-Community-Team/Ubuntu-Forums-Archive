---
title: "MSI Starcam 370i"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by gilligan_bdg on 2006-01-05
Has anyone ever tried the MSI Starcam 370i under Ubuntu or Debian?  This camera would be a good fit for a project I'm doing, but I haven't been able to dig up any information about Linux support.

---

### Post by n0ah on 2006-01-10
I'm curious as well.. I just found one of these for a good price and was wondering if it'd work at all.. my Quickcam Messenger won't work in x86_64 so far.. and I'm too frustrated to work with it, but I want a decent cam and that one looks good..

-D

---

### Post by gushy on 2006-06-14
any update to this?  I've just come across this cam and it certainly looks like a good product.

---

### Post by gushy on 2006-06-21
well I bit the bullet and bought one, can't get it play nice on my 6.06 server box, even with the latest spca5xx module. :(

cam is fine cos I just tried it on my windows box. grrr.

---

### Post by theonhighgod on 2007-09-23
the answer seems to be yes :

[http://ubuntuforums.org/showthread.php?t=320433](http://ubuntuforums.org/showthread.php?t=320433)

there seems no solution, i have the same camera and have been playing for a while and have gotten no where,

ne help would be welcome but im inclined to go out and buy one from this list: [http://www.fsf.org/resources/hw/cameras](http://www.fsf.org/resources/hw/cameras)

:(

---

### Post by bobe84 on 2008-04-03
I patched gspca driver so now it works with MSI Starcam 370i. I you want i can send you gspca driver that is working with camera...

---

### Post by gushy on 2008-04-03
That would be great thanks.  How big is the patch?  Could you attach to a post here so that others can access it too?

---

### Post by bobe84 on 2008-04-03
Dunno to make patch, anyway go to 
[www.pamplast.com/gspca/](www.pamplast.com/gspca/)
i uploaded it there...
If you have problems please let me know so i can fix it...
It would be nice to have some kind of feedback.
Right now driver is working fine in dark environments.
Auto expo and auto gain are working but needs to improve that.
Also there is problem when i turn my camera to monitor where is located konsole(black background and white text), camera starts to "choke" and eventually get kernel panic.
My guess is that problem lies in gspca driver and needs to be worked on.
Please let me know if there are some problems or if it works at all.

---

### Post by OliW on 2008-04-09
Site appears dead now (403).

---

### Post by bobe84 on 2008-04-09
My mistake, forgot to upload .htaccess :) works now

---

### Post by GBee on 2008-06-11
Bobe84, can you do a walk through a a newb on how to compile the driver once dl'd? Cheers

---

