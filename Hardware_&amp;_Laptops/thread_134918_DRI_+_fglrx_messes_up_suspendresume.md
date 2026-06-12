---
title: "DRI + fglrx messes up suspend/resume"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by jakemikey on 2006-02-22
I've got a Compaq Presario V2555US with a Ati Xpress 200M GPU.  In the process of getting Ubuntu set up just the way I like it, I noticed that suspend stopped working - rather, resume stopped working.  Suspend to RAM worked okay, but when I opened the lid, the display locked up as has been frequently described.

I tried to locate the culprit, and found that the following scenario is repeatable:

DRI loaded in xorg.conf = resume doesn't work
DRI not loaded in xorg.conf = resume works

I'm using the fglrx driver because nothing else works.  I'm using DRI because, well, I don't get any acceleration without it. 

How can I keep fglrx + DRI and still be able to suspend/resume?  I noticed that in /etc/default/acpi-support it gives the option of unloading certain modules before suspend, but with lsmod I don't see a DRI module loaded, just fglrx.  I tried to add the fglrx module to the "remove before suspend" list, but I still had the same symptoms.

Thanks for any help.

---

### Post by jakemikey on 2006-02-23
Okay just solved the problem after A TON of reading.

1. Downloaded the latest fglrx driver from ATI (8.22.5 right now)
2. Ran the installation script and generated the .debs
3. Followed the instructions at [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)
...the section "using drivers from ati.com"

Followed those instructions exactly and now I have suspend AND DRI!!! Woo hoo!

---

