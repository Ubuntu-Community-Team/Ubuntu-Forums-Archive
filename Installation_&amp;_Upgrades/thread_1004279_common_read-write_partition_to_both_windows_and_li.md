---
title: "common read-write partition to both windows and linux"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by frejock on 2008-12-07
Heya there,

I've been experimenting with dual boot for a while and since I intend to do a complete reinstall, I'd like to seek some collective wisdom from the forum

My requirements:
1. A /home partition that should allow install me to uninstall/install/update all Linux software
2. A Data partition that will allow read-write from both XP/ubuntu
3. A windows partition for XP - I noticed some online financial sites I use are bit about IE, which is why I want to keep XP on. Also wifey uses my laptop at times and prefers XP. So I'd like to have XP with minimal apps.

Thoughts:
A) I use an Acer aspire 5510 and so far Gutsy worked well on it. I havent tried newer versions yet but any recos would be fine..I'll either install the new ones or upgrade.

B) My HD is 120 GB so I was thinking of the following:
-15 GB partition for XP(NTFS - or should it be fat? I intend to keep only software, not data)
-2.5 GB swap partition for Ubuntu
-Ubuntu partition for /home(what size should this be?)
-Common DATA partition(this is my biggest concern : would ext3 support r/w on both XP/ubuntu?)

I appreciate your thoughts, thanks in advance :)

-FH

---

### Post by Nathan Sweeney on 2008-12-07
For your "DATA" partition, you will want to format as vfat (FAT32).  I've had a 5 year absence from linux, and from what I gather, NTFS is now readable *and* writeable from within linux, but I have never tried to write to NTFS from any os other than windows.  I know vfat will work for both.

15 GB for XP is fine, and 2.5 GB for swap should suffice.  As for your /home, that is up to you.  It seems that you are expecting to install and update software to /home, but that is not what /home is for.  If you use apt or Synaptic, your software is not going in /home.

/home is for your personal settings and documents.  If you have a /data partition mounted, and plan to keep your files there (music, documents, videos, etc), then your /home will not have to be very large.

Personally, I always do the 'wrong' thing and have whatever space I want for linux and mount it all as /.  I never really got into the whole idea of trying to figure out how much to give each partition, so I just do that.

---

### Post by falcon61102 on 2008-12-07
As Nathan Sweeney mentioned, it is possible to read and write to NTFS.  I read and write to NTFS partitions from within Ubuntu quite regularly without any issues.  

If you make your Data partition Ex3 you will need an app for WinXp to be able to read/write but if you go with NTFS or Fat, nothing extra is required.

---

### Post by frejock on 2008-12-07
Thank you for your inputs Nathan and falcon :)

So I guess I will reinstall XP first creating a 15 GB NTFS partition for XP system files, an 82.5 GB NTFS Data partition(which would be the common partition for XP and Linux), and free space of 22.5GB.

After that install Ubuntu creating a 2.5 GB for swap and then all the remaining space(20 GB) to be used up in an ext3 partition for linux. Would this work out fine? I just want to ensure the rest of the partitions(2 ntfs, 1 swap) would be intact whenever I choose to upgrade the ext3 partition.

Is my understanding right? 

Thanks guys.

---

### Post by Nathan Sweeney on 2008-12-07
> **frejock said:**
> Thank you for your inputs Nathan and falcon :)

So I guess I will reinstall XP first creating a 15 GB NTFS partition for XP system files, an 82.5 GB NTFS Data partition(which would be the common partition for XP and Linux), and free space of 22.5GB.

After that install Ubuntu creating a 2.5 GB for swap and then all the remaining space(20 GB) to be used up in an ext3 partition for linux. Would this work out fine? I just want to ensure the rest of the partitions(2 ntfs, 1 swap) would be intact whenever I choose to upgrade the ext3 partition.

Is my understanding right? 

Thanks guys.

That should work fine :)

---

