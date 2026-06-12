---
title: "Switching to ubuntu from xp, just purchased external hard drive"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by stevedyndiuk on 2009-01-29
So I have been using ubuntu for about a week, and love it.  I currently have my 100gb hdd partitioned  80gb -xp and 20gb-ubuntu 8.10.  I just wanted to try out ubuntu installed on hdd.  What I want to set up is a dual boot system with say 70gb partioned for ubuntu and 30gb to xp.  I have about 50gb of jpegs, video, mp3s on the windows partion.  I have purchased a 500gb usb hdd.  This is my plan:  Completely wipe my 100gb hdd.  Install ubutnu as primary OS.  Install xp as 2nd OS with dual boot.  I would love to be able to use all of my data with both OS, and access my data on external hdd with both OS's.

What I'm getting at is, Where do I start?  What should my usb hdd be formatted as?  Should it be partitioned for each os?  Should xp or ubuntu be installed first?  I need to be able to backup from windows and then move data back in.  is there a paticular version of ubuntu i should use?

I would consider myself fairly proficient with computers and xp.  I am a complete n00b with linux.  That being said I have managed to fix my broadcom wifi and my sound in ubuntu with help from this forum.  So here I am asking for all of your expertise again.  It took me a long time to understand that it is easier to ask for help before the disaster begins.

gateway mx7515
amd athlon 64 4000+
1 gb ram
ati x600 video

---

### Post by dstew on 2009-01-29
> What should my usb hdd be formatted as?If you want it for storage that can be read and written by both XP and Ubuntu, it should be vfat (or FAT32 in Windows-speak). It is also possible to use NTFS, but you need to install [third-party software to write NTFS from Ubuntu**]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G").> Should xp or ubuntu be installed first?Install XP first. If you install XP after you install Ubuntu, it will destroy the Ubuntu partition.> is there a paticular version of ubuntu i should use?With your processor, you can use either the 32- or 64-bit versions. The 32-bit might be a little more solid, and the 64-bit a little faster in some applications.

**Actually, the software is pre-installed on 8.10, but you need to install the configuration program to use with the graphical interface.

---

### Post by stevedyndiuk on 2009-01-29
thanks, that makes perfect sense.

---

