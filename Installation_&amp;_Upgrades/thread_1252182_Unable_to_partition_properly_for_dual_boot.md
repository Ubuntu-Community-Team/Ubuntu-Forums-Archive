---
title: "Unable to partition properly for dual boot"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by rmcellig on 2009-08-28
I made a copy of 9.04 to CD and when I boot up on my PC into the Installer, when the partition window comes up, I don't have an option to create a side by side partition. I am totally confused as to what to do next based on the enclosed screenshot.

I really want to get Ubuntu 9.04 up and running on my PC, so that I can dual boot into either XP or 9.04. Thanks!!!

I don't remember it being this complicated in 8.10. I just watched a video of how to setup dual boot in 9.04 and the window looks totally different.

---

### Post by enli on 2009-08-28
Choose "Specify partitions manually (advanced method)". I guess you know the partitioning as you mentioned watching a video about it.

**EDIT:** It looks like there are no partitions on it. So you will need to create the partitions for both XP and Ubuntu.

For XP : create ntfs partition
For Ubuntu : create ext3/4 partition and swap partition.

First install XP and then Ubuntu or else you will face booting issues. Nothing to be scared of but it is much easier if you install XP then Ubuntu.

---

### Post by rmcellig on 2009-08-28
I did that but I am not sure exactly where to go from here.

---

### Post by rmcellig on 2009-08-28
I keep getting the following error:

No Root File System Is Defined

Please correct this from the partitioning table

I also tried installing  wubi.exe and I still get the above error. What should I do?

---

### Post by stlsaint on 2009-08-28
> **rmcellig said:**
> I keep getting the following error:

No Root File System Is Defined

Please correct this from the partitioning table

I also tried installing  wubi.exe and I still get the above error. What should I do?


ok consider this...dont install ubuntu yet...first make the partitions of how you want them...200 for xp 150 for ubuntu or whatever...then install xp first on its own partition...then install ubuntu...on its own partition that way you wont have to deal Grub issues...also you have to make two partitions...thats why you keep getting the error...you must make a root (/) and swap partition...you set them both in the partition editor...you can check my signature on dual booting which shows how it goes with xp and ubuntu with xp installed first...but it will guide you through either processes!

---

### Post by presence1960 on 2009-08-28
Is XP already installed on your machine? if it is I would use [gparted Live Cd]("http://gparted.sourceforge.net/livecd.php") to shrink XP's partition and create room for Ubuntu. Then create the Ubuntu partitions (at minimum / and swap). Then boot the Ubuntu Live CD and select the manual option. Then highlight each Ubuntu partition and click edit. Set parameters such as Use as (filesystem), mountpoint: / for Ubuntu root and /home if you created a partition to use as separate home partition. For swap set use as to linux-swap.

If XP is not installed create an NTFS partition for XP along with the linux partitions for Ubuntu. Install XP to the NTFS partition then install Ubuntu as described above.

---

