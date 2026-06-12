---
title: "Dual Boot Problems"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by captaino on 2009-01-01
I am an Ubuntu novice.  I installed Ubuntu 8.10 just last night to my existing Windows XP system.  I have two hard drives so i decided to dedicate one to Windows and one to Ubuntu.  Ubuntu loads and works fine. On the other hand,  when I choose to boot up in Windows it gets to the login screen and I am able to login and the background and mouse appear on the screen but nothing else.  The processor sounds like it went inactive after getting the background loaded.  Any answers or tips would be appreciated.  I am currently running a custom built pc with a MSI 7093 motherboard, and a AMD 1.8 MHz processor with 1 Gb of RAM.

---

### Post by award982 on 2009-01-02
this is not a dual boot problem,this is a windows problem,or linux just messed it up.you should over re-install windows and then boot from a ubuntu boot-floppy (boots from hard drive) and somehow reinstall grub,or if you dont have important files i suggest u format the drive.
 
and one more thing-it would be best if you dont use two harddrives,its better when using partitions.

---

### Post by captaino on 2009-01-03
thanks.  I think i know what went wrong now.  When I installed Ubuntu I also had it import my documents and settings from the other hard drive and I am thinking thats what messed it up.  Oh and the reason I used two separate hard drives is because my current hard drive wasnt large to begin with.  But thank you for your help.

---

### Post by DeMus on 2009-01-03
> **award982 said:**
> this is not a dual boot problem,this is a windows problem,or linux just messed it up.you should over re-install windows and then boot from a ubuntu boot-floppy (boots from hard drive) and somehow reinstall grub,or if you dont have important files i suggest u format the drive.
 
and one more thing-it would be best if you dont use two harddrives,its better when using partitions.

Why are two partitions better than two disks? What is the difference?

Demus

---

### Post by award982 on 2009-01-04
> **DeMus said:**
> Why are two partitions better than two disks? What is the difference?
 
Demus
 
 
some harddrives conflict with each other, (verry rarely though,) or the computer doesnt accept more then one (ibm,some compaq models).i had this one case when ive had one 30 gb maxtor and 80gb samsung hdd and whenever ive installed linux on the 30 gb (secondary drive) hdd the grub allwais wasnt working,it simply didnt see the drive or thought there was no files to boot from
 
though,this not all times happens,or maibe its another problem

---

### Post by award982 on 2009-01-04
> **captaino said:**
> thanks. I think i know what went wrong now. When I installed Ubuntu I also had it import my documents and settings from the other hard drive and I am thinking thats what messed it up. Oh and the reason I used two separate hard drives is because my current hard drive wasnt large to begin with. But thank you for your help.
 
 
sure,no problem

---

