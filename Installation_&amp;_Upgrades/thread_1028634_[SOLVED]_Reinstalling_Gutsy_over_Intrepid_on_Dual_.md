---
title: "[SOLVED] Reinstalling Gutsy over Intrepid on Dual Boot system"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by sanford55 on 2009-01-02
Thanks for the help on my previous question.  I have a new one.  I dual boot XP and Ubuntu and want to go from 8.10 back to 8.04 since 8.10 does not work well with my NVIDIA graphics card.  I started the install from the Live CD, but ran into a possible problem.  Maybe it is not a problem, but I am still a newbie with Linux and have seen a number of installations go bad for other folk I know.  

In the past, when I upgraded from one Ubuntu to the next, I reached the point where it asks about my hard drive partitions.  If I remember correctly, it was easy.  There was a window titled "prepare disk space" with a graphic that  showed my windows partition and my ubuntu partition and installing the new ubuntu over the old one simply happened.  Now, when I reach the partition stage, the graphic does not show my XP partition at all and it looks like it wants to install 8.04 in yet another partition next to 8.10 rather than over it.  There are options to take manual control over the partitioning, but I am sure I never had to do that before and would hate to screw it up. Any help would be much appreciated.  Sanford

---

### Post by Elfy on 2009-01-02
Run this in a terminal

```
sudo fdisk -l
```

It will tell you which are linux partitions and which others.

Use the manual option to pick the existing linux partitions - if you had a default install to start with you probably only have 1 linux and 1 swap.

If you need help post back with the result of the command

---

### Post by Sef on 2009-01-02
> Run this in a terminal

 	Code:
 	sudo fdisk -l 


l is a small L.

---

### Post by sanford55 on 2009-01-03
Thanks for your helpful response, I ran the "fdisk -l" command and got this. I have a Linux partition and a linux swap partition.  I am not sure what the extended partition is or whether it is part of linux.  When I reach the partition screen when I reinstall Gutsy, and I choose manual, I assume I just tell it to do the Linux partition.  Will it automatically pick out the right place to put the new swap partition or do I have to tell it that as well?  Is this all that I need to run the manual partition?  Thanks.  Sanford


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4416    35439390    7  HPFS/NTFS
/dev/sda3            4417        7169    22113472+  83  Linux
/dev/sda4            7170        7294     1004062+   5  Extended
/dev/sda5            7170        7294     1004031   82  Linux swap / Solaris

---

### Post by Elfy on 2009-01-03
Run manual - select sda3 - Edit partition - Choose a filesystem, default is ext3, let it format it. Choose a mountpoint - /

That's it - swap will deal with itself. Comtinue with the remainder of the install.

---

