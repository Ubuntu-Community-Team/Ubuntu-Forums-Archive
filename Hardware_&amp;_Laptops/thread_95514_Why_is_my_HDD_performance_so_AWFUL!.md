---
title: "Why is my HDD performance so AWFUL?!"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by artinla on 2005-11-26
I have 3 HDD's (2 SATA and 1 IDE) on an ASUS SK8N mainboard.  It has an NForce3 chipset, and a Promise RAID controller.  (I am not using the RAID)  

The SATA drives are absolutely as slow as molasses.  The IDE drive is not much better.

I know about using hdparm to enable dma, 32 bit, etc.. that is not the issue.  With all the tweaks I can find, the HD performance is just poor.  10 gig from one drive to another might take 5 min in Windoze, takes 30 on my system.

Anyone know of some legitimate fixes for this?  Will there ever be better kernel support for SATA?  

I would sure like to be able to say that Linux performs as well as Windoze on my system, but that would be a lie.  I enjoy Linux, but the performance needs a boost for my hardware.

---

### Post by artinla on 2005-11-27
Update:

I just copied a CD image ~650 Meg from one partition to another.  In Windows it took 30 seconds.  In Ubuntu, it took 4 minutes.

---

### Post by Bandit on 2005-11-27
That is strange. Have you tried switching the controler card out for another? Sounds like that control card isnt being fully recognized or something.
Cheers,
Joey

---

### Post by hw-tph on 2005-11-27
What is the output of **hdparm -tT /dev/hdX** (where hdX is the name of the disk)? That command will give you a pretty good idea of what kind of HDD performance you get.


H&#229;kan

---

