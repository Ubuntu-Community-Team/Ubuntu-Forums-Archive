---
title: "Need Help recovering XP dual boot after Ubuntu 8.04 install"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by Robb.Pryor on 2009-06-25
I installed 804. on my Windows XP laptop.  I had intended to make it dual boot, but instead I wiped out my XP installation.  I have a backup archive of the entire disk just before the ubuntu install (created with apricorn EZ GIG II) on an external HD.  I think it has the windows setup files as part of the backup.  How do I recover XP with dual boot?

It would seem that I need to:
  1) Re-partition the disk as intended (but I'm not sure how best to do this.)
  2) Create/obtain an XP boot CD (but again I'm not sure how best to do this.)
  3) Copy the backup archive files onto the new partition
  4) Set up dual boot capability (and again I'm not sure how to do this.)

---

### Post by Herman on 2009-06-26
Are you sure you actually deleted/overwrote your XP partition?
Have you looked with a partition editor and checked to see if it's really gone?
Maybe the only problem is it hasn't appeared in your boot menu?

Can you boot your Ubuntu Live CD and go look? Open 'System'-->'Administration'-->'Partition Editor', (GParted), and see if you can still see any partition(s) containing either FAT32 or NTFS file systems.

Another way to see what's in your partition table is to open a terminal, ('Applicatins'-->'Accessories'-->'Terminal', and type, (or copy and paste in), the following command,
```
sudo fdisk -lu
```If you can post the result from that command here, it might help someone to help you.

---

### Post by Herman on 2009-06-26
> I have a backup archive of the entire disk just before the ubuntu install (created with apricorn EZ GIG II) on an external HD. I think it has the windows setup files as part of the backup. How do I recover XP with dual boot?I'm not familiar with the software you have used for making your backup. You'll need to read the docuentation for your backup software to learn how to restore with it. Did it come with some kind of a Live CD, or how does it work if Windows XP is deleted? I would just concentrate on restoring your old Windows XP and then re-install Ubuntu again later. It only takes about half an hour to install Ubuntu.
> Re-partition the disk as intended (but I'm not sure how best to do this.)Look in my sig link near the bottom of this post, it will lead you to a website where you'll see several different ways to install Ubuntu with illustrations.
> Create/obtain an XP boot CD (but again I'm not sure how best to do this.) If you only need a boot CD, (meaning  a CD that will boot Windows XP, I recommend Miles Comer's NTLDR CD, from this website here, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"). If you're talking about a Windows XP Installation CD then I don't know.
> Copy the backup archive files onto the new partition See your apricorn EZ GIG II documentation I guess?
> Set up dual boot capability (and again I'm not sure how to do this.)     Someone here will help you or see my sig link.
Wait until we're sure you really deleted your XP first though.

Do you really need Windows XP for something? Why not just forget about it? Ubuntu's better! :)

---

### Post by Robb.Pryor on 2009-07-07
Thanks for the suggestions and information.  I did indeed wipe out my Win XP installation.  I tried to re-partition the disk so I could install Win XP along side Ubuntu, but was not able to get that to work.  In the end, it was simpler to restore the disk to pre-ubuntu state, using the apricorn CD and the backup copy of the C:\ drive I made just before installing ubuntu, and then re-installing ubuntu manualling re-partitioning the disk for dual boot.  It's all working now and everything is fine.

---

### Post by Herman on 2009-07-07
:) Cool! Congratulations on your success!

---

