---
title: "Network keeps failing"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by igknighted on 2007-03-01
I recently reinstalled Ubuntu 6.10 due to new hardware, and now my network likes to cut out all the time.  I can get it back by using a quick ifdown eth0, ifup eth0... but its really annoying and I can't download any large files because it often cuts out in the middle and they won't restart.  Any ideas on how to clear this up?  It's an nForce 550 chipset by the way.

---

### Post by timmir on 2007-03-01
Has this network card ever worked with other software.  I had a similair problem that I fought for months and it turned out that my router's firmware was a small bug that was only triggered by my ISP's settings.  I don't know much about your chipset, but I know some things to ease the pain.

1. use wget to download large files.  It has a resume feature so that you can resume large downloads.

2. install network manager.  It's a little more automatic than ifup/down and even if it doesn't reconnect automatically, you only have to click the icon to reconnect.

good luck

---

