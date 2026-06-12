---
title: "very very slow speed BCM4318"
date: 2009-12-08
forum: Hardware
---

### Post by 7450 on 2009-12-08
Hello everybody.
I have a problem with wifi BCM4318. Transfer speed is very slow.(The dial-up was faster) My laptop is Asus A6000 Series, Semprom 64-bit, ubuntu 9.10.
Thanks.

---

### Post by lownox on 2009-12-08
I have the same wireless card as you.  Check out this procedure.  You need to use the B43 drivers first and let it not work... then follow this procedure and enjoy your wireless.  I hope this helps.
[http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/](http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/)

---

### Post by brookie on 2009-12-09
> **lownox said:**
> I have the same wireless card as you.  Check out this procedure.  You need to use the B43 drivers first and let it not work... then follow this procedure and enjoy your wireless.  I hope this helps.
[http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/](http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/)

lownox, before I try that guide I wanted to ask if you got the 4318 to connect to a hidden ssid. Using Karmic and b43xx cutter it works out of the box for wireless networks that broadcast their ssid, but it will not connect to a hidden ssid.

---

### Post by lownox on 2009-12-09
I haven't tried it with a hidden ssid.  However, I found that the b43 drivers were fast, then slow, fast, then slow.  I kept having to hit the wireless button on & off to get the card going again.  The ndiswrapper method works normally.  I will hide my ssid later and report back... wife is online right now and I dare not touch the router config.

---

### Post by brookie on 2009-12-10
Thanks lownox but I think I figured out that my problem is actually a but in Network Manager not being able to connect to hidden networks because buttons are grayed out. Check my post here:
[http://ubuntuforums.org/showthread.php?p=8473753#post8473753](http://ubuntuforums.org/showthread.php?p=8473753#post8473753)

---

### Post by 7450 on 2010-02-07
Thanks all.
My resolution is new kernel 2.6.32 .;)

---

### Post by watersoup on 2010-07-20
bump !!!

has any body found the validity of the kernel mentioned above.

thanks

---

