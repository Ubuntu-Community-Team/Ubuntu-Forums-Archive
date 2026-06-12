---
title: "Wireless problems"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by Z_o-s-o on 2007-12-05
I'm having some problems with wireless on an HP Dv6000 laptop.

The card is a Broadcom Bcm4311 and I'm using the restricted driver.  The firmware being used is wl_apsta.o.  The problem is, I'm getting horrible range out of the card for whatever reason.

When using Feisty, I was using ndiswrapper, with good results.

Is there a workaround for this or something I'm missing?

Thanks!
Z_o-s-o

---

### Post by Z_o-s-o on 2007-12-05
Bump.

There has to be a way to fix this....I can't use the laptop wirelessly if I walk more than 10 feet from the router.

---

### Post by TripWire7 on 2007-12-05
on gutsy I couldn't get it to work..... I got it to the point where I could connect but after about a minute I would loose connection..... and thats the closest I got.

Now I went to feisty and I'm working on getting it working now, things so far have been alot easier with this version.... except for the wireless.

Oh I have a broadcom 4311 mcg wireless card on my acer aspire 3680..... I'm starting to think wireless is just a myth..... :(

if I run across anything that may help I'll post it

---

### Post by Z_o-s-o on 2007-12-05
Yeah with Feisty and the Ndiswrapper "easy way" method, it worked just fine, but now with Gutsy on the same PC, the "easy way" no longer works, so I'm stuck using the restricted driver, which connects, and has good throughput, but no range.

Check this out...if you havent already.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by TripWire7 on 2007-12-05
[http://ubuntuforums.org/showthread.php?t=604273](http://ubuntuforums.org/showthread.php?t=604273)  This may help you.  It didn't help me when I was useing 7.10 though.

I'm a step closer for the wireless connection.  I still cant scan for networks, or manually connect to mine, but the wireless light is on so i'm going in the right direction.  Did you do anything else?

---

### Post by Z_o-s-o on 2007-12-05
I haven't tried anything since my last post

---

### Post by Z_o-s-o on 2007-12-05
I found this extremely helpful

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I'm not sure how I overlooked it, but the instructions in that article got me my wireless back, full range, and full speed.

- Z_o-s-o

---

### Post by Ayuthia on 2007-12-05
I could be wrong, but I thought that there is some transmission issues with the 4311 in the 2.6.22 kernel.  I have experienced similar issues when I was using it.  I am currently using the 2.6.24 kernel in Gentoo and it seems to work better.  Right now I am using NDISwrapper for Gutsy.  You might check out [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) and try out their b43 driver.

---

### Post by TripWire7 on 2007-12-05
many thanks Z_o-s-o.   My wireless is now up and running

---

### Post by Z_o-s-o on 2007-12-05
Good to hear.

---

