---
title: "Grub, installing Win7, existing Win XP and Ubuntu"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by tesseract1 on 2009-07-30
So I am planning on installing Win7.  I'm apprehensive because I'm not too familiar with grub and how it works.  My setup at the moment is I have two separate drives one for Ubuntu and one for Win XP.

I want to partition the XP drive and install Win7.  Is there some special process I need to do to get everything setup correctly and to have grub recognize it?

I don't want to jeopardize anything, because I don't have a windows recovery disc to fix the MBR if anything goes wrong.

---

### Post by pmlxuser on 2009-07-30
you need at least the ubuntu disk to reinstall grub when you finish installing windows. if you don't mess the windows partition during the windows installation you will be able to get all in the grub after reinstalling grub.

---

### Post by tesseract1 on 2009-08-11
Are there any HowTo or guides showing me how to do this for my particular situation?  I've had bad experiences playing around with this stuff.  I don't want to mess anything up.

---

### Post by Mark Phelps on 2009-08-11
> **tesseract1 said:**
> I want to partition the XP drive and install Win7.  Is there some special process I need to do to get everything setup correctly and to have grub recognize it?


Safest thing to do is to disconnect the Ubuntu drive, set your BIOS to boot from the XP drive, partition the XP drive to make room for Win 7, boot from the Win 7 DVD -- and do the install.

Win 7 will detect XP and create a boot menu including itself and Win 7.

When you reconnect the Ubuntu drive and set the BIOS to boot from it, your Windows entry (from GRUB) will now launch the MS Windows boot menu -- from which you can then select Win 7 or XP.

---

