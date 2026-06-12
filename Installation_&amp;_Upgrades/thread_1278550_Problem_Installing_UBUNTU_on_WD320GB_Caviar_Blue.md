---
title: "Problem Installing UBUNTU on WD320GB Caviar Blue"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by Radjan on 2009-09-29
Hi, 
I am new to the Linux world. I am trying to get rid of the Blue Screen of Death and was ready to start a fresh install with no dual boot (only Linux) on my P4 2.4GHz, 1Gb Ram PC.

I downloaded and burned UBUNTU CD just fine. Checked the CD with no errors, but when I tried to install I got a Status error code 1, and then a non-iterable disk error. Talking to a friend he said something about my hard drive driver not being correct since it is a fairly new disk.

I have a 320GB WD3200AAJB Caviar Blue Hard Drive.
Was thinking of allocating 80GB on root, 4GB swap and the rest to home.

Any hints or help would be deeply appreciated.
Radjan

---

### Post by RJARRRPCGP on 2009-10-23
Likely causes:

A faulty HDD. 

Your IDE controller don't support 48-bit LBA, thus using the earlier 28-bit LBA -->that means you have the 128 GB limit and thus cannot use a 320 on your motherboard.

---

### Post by Mark Phelps on 2009-10-24
Just curious, did your machine come with the WD 320, of did you buy that later?  I'm asking because of possible BIOS limitation problems if you bought the disk later and your machine's BIOS can't see the full capacity of the drive.

---

### Post by rage9 on 2009-10-24
From 8.10 and on I had major trouble with my old laptop and hard drive.

I just looked up the drive on Newegg.com and looks fairly up to date, which might point you to a mobo/bios issue.  

If you can try and update your bios, do that first.  

If your still having issues try an older version of Ubuntu like 8.04.

---

