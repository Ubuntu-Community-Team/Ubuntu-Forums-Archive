---
title: "Locked out of Windows, Xubuntu only have LIve CD HELP!!"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Okie Dokey on 2009-10-30
Thanks for reading my desperate post.

Here's how I ended up stranded with only a Live CD of Xubuntu to help restore my system.

1) Fresh installed WindowsXP On partition 2 of Disk1 Fat32
2) Installed Xubuntu on SDa3 used Ext3 for installation of root, never did a boot partition or anything fancy, I'm an absolute Linux newbie. The Swap partition is the 4th partion on my disk.
3) partition 1 on the Drive contains data (backed up)Formated in Fat32 (I intended to have it availible for both XP & Xbuntu). There is no space preceedingthe partition.

3) after ubuntu installation I found i could only boot into Xubuntu 9.10, windows was no longer available, I need it back badly. Next I used a recovery module on my Windows XP CD and Used FIXMBR and FIXBoot, strangely the location windows described C:/windows does not exist (the first partition does not contain windows.  Never the less, after performing FIXMBR, I couldn't boot into ubuntu OR windows, leaving me with just teh Live CD for internet access.

I'm totally lost now what to do. I think it was best to be able to boot from a Floppy drive into either OS. This garbage around MBR or whatever always backfires and again i'm stuck and stranded for 3days.

Also I tried last night, while using the installed xubuntu that SUDO command wouldn't work it asked formy password but it didn't let me type it in. Now on live CD it seems I can use it.  I don't know what it means to mount a drive, Gparted says my hard drives are all locked. it seems that my floppy is available, a usb music device Fat32, i suspect If I reboot the Live CD and put in a usb stick that would be available too.

Although I'm lost, currently I'm trying to put super_grub_disk_castellano_floppy_0.9589.img on to a floppy disk hopping I can boot using that (to either XP or xubuntu). However, I can't seem to find an installed app (only have LiveCD) that would open a .img file.and that's as far as I've gotten.  Earlier I opened up the file called menu.1st but it was blank.

Although I can't get into xubuntu anymore either, I believe 1 course of action would be to reinstall xbuntu overtop the orignal installation hopefully that would let me use xubuntu installed, possilby finding a app that can open a .img file to put super grub on my floppy so I can use windows again. i'll take that route until I hear back from the forum.

Also note that I seem to not be able to utilize Apt get with xubuntu installed, I'm aware of the program, but I don't think it comes with xubuntu 9.10.

Please help a newbie with almost no experience .
thanks in advance,
Cam.

---

