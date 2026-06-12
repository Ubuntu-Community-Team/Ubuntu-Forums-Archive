---
title: "Promise SATAII150 S8X"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by SleightfulMind on 2006-03-26
Ok, I am attempting to build a new system using dual opteron 248's and a promise SATAII150 S8X card. I have Ubuntu server installed just fine and I have recompiled the kernel to utilize multi-processor and hypertransporting. I will shortly install that kernel to see if it in fact works but I don't anticipate any problems. The issue came in when I tried to compile the RAID controller drivers. I built the kernel with all the options I needed, extracted the RAID source code and tried to compile it. When I run make, it spews out a bunch of errors about various structures not existing and other structures not having various members etc. In short, it won't compile. I tried altering the source since it was referencing antiquated libraries but I got the same results. So, here's what I need Ubuntu to do:

Recognize my SATA drives that are hooked up to the SATAII150 S8X card. As far as I am concerned, RAIDing will be done with mdadm, I don't care if Ubuntu can utilize the card's onboard RAID features. Basically I just want an 8-port SATA controller.

How can I get the system to recognize the drives?

Thanks in advance for any help!

---

