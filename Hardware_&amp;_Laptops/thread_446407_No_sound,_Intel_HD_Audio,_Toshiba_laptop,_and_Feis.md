---
title: "No sound, Intel HD Audio, Toshiba laptop, and Feisty"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by hondaman on 2007-05-16
Ive gone through as many pages as I can, and I am failing at making ANY sound work. I have a toshiba p105-s9337

I have tried different lines at the end of alsa-base (auto, 3stack,laptop-ea[d, ref, etc).

I have compiled and installed the latest alsa software.

I have checked in alsamixer to make sure its not muted.

I get no sound in anything. On startup. In mp3's. In preferences-> sound testing.

I have tried different mixers and different audio devices.

lspci says:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Can someone possibly have an answer to make my sound work?

Thanks!
Edit/Delete Message

---

### Post by hondaman on 2007-05-16
[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

Thats the fix for me.  Just found it, and works great!

---

