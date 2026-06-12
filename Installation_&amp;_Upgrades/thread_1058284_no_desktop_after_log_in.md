---
title: "no desktop after log in"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by ok1958 on 2009-02-02
I've just been given a desktop made by HP, i've installed Ubuntu 8.10, but once i get past putting in my password nothing happens.  It just hangs with a blank screen and a mouse pointer.

I've looked at some forum posts, and followed some examples, but have had no success.

I logged into the failsafe terminal session and found thsi out about my onboard graphics card;

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

thanks in advance

stu

---

### Post by Partyboi2 on 2009-02-02
Maybe compiz could be causing the problem. Try booting into recovery mode (Press Esc when you see grub loading... at boot and select  recovery mode)  then when you are at the prompt 
```
sudo apt-get remove compiz compiz-core
```
If this does not work you can reinstall those packages with
```
sudo apt-get install compiz compiz-core
```

---

