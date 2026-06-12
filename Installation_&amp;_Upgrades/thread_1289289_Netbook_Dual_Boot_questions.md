---
title: "Netbook Dual Boot questions"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Dr Apnea on 2009-10-12
So I've got a couple dual boot questions for anyone that can help.  I've been lurking and searching the forums but couldn't find my answers so here it goes:
I installed XP SP3, then Ubuntu 9.04.  Things were working smoothly at first.  I made sure each OS opened and functioned in the dual boot.  I then setup programs & settings for each OS.  I didn't have the option when initially installing from the liveUSB to create a NTSF partition, so within Windows I created a NTSF partition for shared storage and migrated the My Documents folder to this drive.  I didn't change or touch any other partitions.  I then did all of the windows updates, and then went to restart the computer and got an error 22 on grub.  After searching around for a while, trying to use the liveUSB to fix grub in terminal, trying superGrub and some other suggestions only to then get Error 17, then no error but GRUB stalls, i finally decided I would waste as much time reinstalling as finding a fix that worked so I reinstalled ubuntu & did all the work arounds again  :mad:([https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)).  It is currently dual booting fine, and settings/programs are how I like it.

My questions:
#1 - what actually ruined my GRUB?  Was it an upgrade or creating the NTSF partition in windows, even though i didn't touch the "/" partition that I believe grub is mapped to.  I want to know so I avoid doing whatever caused it again (even if that means disabling XP updates).  

#2 - Now that I had to waste a bunch of time trying to fix and reinstall GRUB, is there a way to backup that file to a bootable USB so that if GRUB gets messed with I can insert the boot recovery USB and either copy it to the correct location or have it function as the site of my grub files?

#2 - Is it possible to get rid of the unpartitioned 7-8mb spaces on my HDD that show up in GParted? (see below)  They are just annoying and I cannot figure out how to expand the partition into these small sections.

#3 - Would it be possible or even useful to have one of these small unallocated parts of my HDD be a dedicated location for the boot files?  My thoughts here were that if the boot files get messed up I could just have a copy of that entire partion on USB and replace it?

#4 - On the start menu under places it lists the NTSF windows partition.  Is it possible to hide that partition (not merely require a password to mount it like other partitions)so my wife cannot accidentally alter files in it while in ubuntu?  I was thinking something like a ".hidden" file which I use for the windows hidden files that are visible in the Shared Storage partition though Ubuntu.  

Anyway, that was a lot, but if anyone can help answer some of these questions I would really appreciate it.  I have the day off today and will just be trying to fix this thing up for her.  Thanks
-Stephen

My setup is as follows:
Hardware:  Stock Aspire One A0751h
Partitions according to gparted: 
1) /dev/sda1 NTFS 20.51gb for windows
2) /dev/sda2 NTSF 185.99gb for shared storage
3) unallocated 7.84mb
4) /dev/sda3 Extended 26.37gb (see below)
   /dev/sda5 ext4 14.90gb for /home
   unallocated 7.88mb
   /dev/sda6 Linux Swap
   unallocated 7.84mb
   /dev/sda7 ext4 7.45gb for "/" ubuntu

---

### Post by Dr Apnea on 2009-10-12
.

---

### Post by Dr Apnea on 2009-10-13
,

---

