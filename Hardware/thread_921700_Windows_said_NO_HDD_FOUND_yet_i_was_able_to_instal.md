---
title: "Windows said NO HDD FOUND yet i was able to install linux"
date: 2008-09-16
forum: Hardware
---

### Post by faraz_k86 on 2008-09-16
K so here is what happened, I re-partitioned my HDD using GParted, but then when i wanted to install Win XP, during setup it gave me the error that no hard disk found.

k so i tried again multiple times and got the same error.

Then just for the heck of it i inserted ubuntu live cd and started installation, even the live environment ws able to read all the partitions. and it got installed perfectly without any errors on the same HDD.

My Question : **Why?**


also I do **need** win xp so how do i fix this? i used hitachis disk checker and it told me that I have a faulty hardware.

How do i find the fault and isolate it? is there any software for that?

---

### Post by dasunst3r on 2008-09-16
If your computer's hard disk is connected using SATA, that may be why.  Windows XP's installation routine probably does not have the drivers needed to recognize the controller.  Thus, no access to controller = no access to hard disk.  To the best of my memory, there should be a setting in the BIOS to place the SATA controller into a compatibility mode of sorts.

---

### Post by faraz_k86 on 2008-09-16
but how was it able to operate normally before the re-partitioning?

---

### Post by faraz_k86 on 2008-09-17
c'mon guys. im sure there is a solution or software for my simple problem :)

help me out :)

---

### Post by faraz_k86 on 2008-09-17
i so hate it when im on everyones ignore list :(

---

### Post by MegaJim on 2008-09-21
Whoever installed windows before you got the computer used a disk from the manufacturer or a disk image to install XP.

---

### Post by ugm6hr on 2008-09-22
> **faraz_k86 said:**
> also I do **need** win xp so how do i fix this? i used hitachis disk checker and it told me that I have a faulty hardware.


If that is true - I suspect that it is a hardware problem.

As for Windows not "seeing" a HD - SATA drives appear to cause problems, altho I have found that HD partitions in ext2/3 etc format are ignored.  Not sure why.

In any case - if the Hitachi disk checker says there's a problem, I'd save yourself future heartache by just replacing the HD.  I had a similar problem in my old laptop: blamed Windows, installed Linux (which worked), until the HD finally refused to boot anything.  Fortunately, a live CD allowed be to save all my data before it died.

The GParted use may be coincidence.

---

### Post by Ng Oon-Ee on 2008-09-22
As I recall, when I first installed a SATA hard disc on my desktop I was able to create a bootdisk which flashed my BIOS into recognizing the hard disc.

You'd have to search for something like that for your HD though.

---

