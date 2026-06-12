---
title: "Want to format external Hard drive"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by ChopperX on 2009-05-25
Ok here is the story. I use vista and just today it decided to update itself which is fine. Upon reboot it configured itself like it usually does to finalize the update. It rebooted again and my monitor wouldnt work at all. I shut the computer down and turned it back on and the monitor worked. Vista said that the configuration failed. It keeps doing the same crap over and over again.

So i decided to create a Ubuntu Live CD and use that to back up my hard drive since i cant get into windows. Right now im running off the live CD and i plugged in an external LaCie hard drive using the USB connector. Linux sees the hard drive and i can access it. Problem is i want to format it properly so that way when i take it back to vista after i reformat my main hard drive all my files will be back.

How do i format an external hard drive in ubuntu 9.04 to work with vista?

---

### Post by taurus on 2009-05-25
You can use gparted (System -> Administration -> Partition Editor) to reformat your external drive to ntfs filesystem.  Of course, you must first unmount it before you can reformat it since you cannot format a drive while it is still mounted.

---

### Post by Therion on 2009-05-25
Simply format the external drive using the NTFS file system.  The Partition Editor (System/Administration) should be able to do that.

---

### Post by whoop on 2009-05-25
If you want to create ntfs partitions be sure to install:
libntfs10
ntfsprogs

---

### Post by ChopperX on 2009-05-25
So i so go into GParted and format the drive to NTFS and that will allow it to work with vista?

---

### Post by Therion on 2009-05-25
> **ChopperX said:**
> So i so go into GParted and format the drive to NTFS and that will allow it to work with vista?
Yes.  

You'll be able to use the drive, formatted with NTFS, from within Visa.

---

### Post by networm1230 on 2009-05-25
hello friend

I just wipe my tow hard drives like to days ago it is vary easy to do I was duel booting vista and Ubuntu Linux but in tow different hard drives but now i am using Linux Ubuntu I no longer have vista installed on my PC. will hear are the steps. before you star you must know a few things. Windows uses fat32 and NTFS file system. Linux uses swap file system.

step.1 In Ubuntu Linux go to Applications than to Add/Remove.

step.2 now select (ALL) and ware is says show chose (ALL available applications)

step.3 now ware it says search. search for (Gnome Partition Editor) click in the box and hit Apply to install it

step.4 now to system than go to (Administration) now go down to (Partition Editor) and click on it

step.5 you must unmount you hard drive if it is mounted now click on (Gparted) that click on (refresh device) this will scan for your hard drives.

step.6 now click on (view) and click on both options. how to the small picture of a hard drive.  and chose your driver that you wont to format too (warning) pleas be careful select the right hard drive you wont to Partition of format look at Device information to mack share you chose the right Drive to format.

step.7 now right click on the big bar that say your mount point of you hard drive and space of your hard drive. Right click on the big bar and go to (format to) and choose your format and click apply. (Warning) this will erase all data from the drive.

NOTE:Remember the the operation system. Windows uses fat32 and NTFS file system. Linux uses swap file system.


Hope this helps you friend good luck!

---

### Post by ChopperX on 2009-05-25
Well thanks for all the help everyone. You have been great. I have used linux in the past but that was like over a year ago so i forgot quite a bit. Back to being a noob :D

---

