---
title: "GRUB Error 17 after booting from GPartEd CD"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Peter108 on 2009-01-03
Hi.

I've searched for the fixes to this, but none seem applicable.  I created a GPartEd CD in order to resize my partitions.  On first boot from the CD, I get

GRUB Loading stage1.5.
GRUB Loading, please wait...
Error 17

At that point I am COMPLETELY hosed.  I'm sorry b/c I don't understand the other posted solutions which say to go into the GRUB menu.  I can't do ANYTHING beyond this.  EVEN IF I go into setup and change/verify that the boot order is CD first, then try to boot off the WIN XP recovery disk, GRUB intercedes and throws the same error.

The only reason I don't use an Ubuntu CD is, b/c, frankly my intent was to expand the Win partition to blow away Ubuntu, as I never succeeded in getting the wireless to work, despite many hours and much help from this forum a few years back.  But that's another story.  For now, I have an unusable laptop, and sure would appreciate some guidance.  I could, I suppose, create an Ubuntu CD on another machine and try to boot off that, but if GRUB is going to muscle in front of that, what good will that do?

1. Yikes!
2. Help!

Peter:confused:[-o<](*,)](*,)](*,)

---

### Post by melojo on 2009-01-03
you must not have cd booting first or something is wrong with the xp cd because booting from cd first will by pass grub.  I would find another xp cd or download supergrub disk and try again.  Also make sure you have the system to boot from the cd first, this is likely the problem.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download it to repair windows mbr

If you can get it to boot xp cd at the recovery prompt

type
fixmbr and then fixboot

---

### Post by Peter108 on 2009-01-04
Of course you were right.  While in setup, I thought that arrowing down to the preferred boot device and pressing enter would promote it to the top of the order.  Wrong!#-o  I needed to arrow down to the CD/DVD Drive, then use F5 to promote to the top of the list (i.e., so that it *displayed* at the top of the list.

I then went in rebooted used the supergrubdisk to set things right.

Thank you for your help!

---

