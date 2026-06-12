---
title: "My late experience with flash drives. Does Ubuntu have trouble with them? Please help"
date: 2008-10-08
forum: Hardware
---

### Post by cnbiz850 on 2008-10-08
I haven't used flash drives for a couple years.  Back then the flash drives seemed to be very reliable, -- I used them to back up some files,etc.  Or should I say Windows is very reliable for that matter since I used flash drives mostly with Windows then.

Now I mostly use Ubuntu (now Hardy).  Lately I thought to use flash drives to transfer some of my digital music to my hi-fi stereo system (I have a DVD player that takes USB input).  So I went out and bought a few flash memory related things.

First I bought an MP3 player with 1GB storage.  Then discovered that I can only load up to some 400MB stuff on it.  I searched on the net and according to some suggestions, I tried reformat it with GParted.  At first, somehow GParted complained that it can not do format on the drive.  So I had to create a new label of "msdos" and then create a new partition which took the whole drive.  Then formatted to FAT32.  Then I found that I could load stuff on it up to 1GB, which is good.  I could also use my DVD player to play the stuff I loaded on the storage, which is also good.  But then I discovered that the MP3 player itself does not work.  It said that it can not find any file on it.  I am not sure what went wrong.  I might have tried fatsort (a program that is supposed to reorder the files alphabetically) on it sometime earlier but it failed and so I reformatted the drive again.   I can't say that was the problem, so I went to talk to the retailer.  Luckily, they changed a new one for me since I had just bought it a couple days earlier.  The new one works with the full 1GB storage for some reason so I load some stuff on it and didn't try to mess with it more.

Then I bought a flash drive (Sony).  Tried loading stuff on it and did fatsort a couple times and foldersort (a Windows program I could try with Wine).  (I had to try to sort the files as the DVD player does not sort the files so it plays the files based on the order that they were stored on the drive and for some reason Nautilus copies file in random order)  Fatsort failed miserably every time.  I had to conclude that it does not work at all.  Foldersort sometimes worked but failed most of the time.  Every time either of programs failed I had to reformat the drive because they totally messed the file system on the drive.  Sometimes I used Gparted and sometimes I used the XP formatter.  At the end, I discovered that the file system was basically not usable -- everytime I load some stuff on it then after I umount/eject/remounted the drive, the some filenames were corrupted such that I couldn't remove them.  Again, I couldn't think of anything wrong but blamed on the quality of the drive hardware.  So I went to the retailer again and demanded that they change one for me.

They changed for me a Chinese Geil brand one that has 3 year guarantee.  With this one, I didn't do any formatting or sorting.  Just loaded up with music files.  I could go to the full 2GB with the storage.  I did copy/erase twice since I got it.  In order to solve the file order problem, yesterday I made a shell script that copies files one by one with the right order on it.  It worked as it is supposed.  The files were at the right order when I played on the DVD player.  But then the new problem is that I can only load up to some 400MB and can go no further.  It is not the problem of the script for sure as doing it by hand with Nautilus is the same.  I did remove something like the .T0001 folder (which I believe holds the deleted files) from the drive.  No luck.

Could anyone please explain what is going on?  Are the flash devices in such bad quality?  Or is it that Linux does something wrong with them?

----------------
Oct. 19: Today, I removed everything on the Geil with command "rm -rf *" and then try to load other stuff on it.  This time, it went up to about 580MB -- more than last time for some reason, but still far from its 2GB capacity.  Then I booted to Windows XP.  XP could access the files on it without problems.  I tried to copy some more files on it from XP.  It didn't complain and succeeded.  But there was something strange I forgot exactly what.  After that, I had to reboot XP -- the usual annoying Windows stuff (it updated itself and demanded a reboot).  Then after reboot, XP said that the Geil was not a formatted device and needed a reformat.  I don't know why, but I did with FAT32.  Then coming back to Ubuntu, I now could load stuff on it to its full capacity.  

I will try more to get further info.  I currently suspect the erase operation in Linux (both from Nautilus and from the command line) causes something wrong with the partition on the device.  This may be because Linux can't really handle this type of device well.  In other word, there might be some bugs in Linux on this (my system is fully updated with Hardy).  The following post regarding fdisk output is very strange.  Though I don't quite understand it, notice what it says "This doesn't look like a partition table  Probably you selected the wrong device."  I did check with "fdisk -l" again after XP reformatted it.  The result is very much similar -- fdisk complains about the partition table as before.

---

### Post by cnbiz850 on 2008-10-08
Just to add.  Now I did "fdisk -l" and got the following on the Geil flash drive:.  Seems something wrong, but I am not sure how it's supposed to be.

```

Disk /dev/sdg: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   ?      435740      852923   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(435739, 33, 45)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(852922, 31, 29)
Partition 1 does not end on cylinder boundary.
/dev/sdg2   ?      340549      478536   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(340548, 59, 47)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(478535, 44, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdg3   ?      137991      495994   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(137990, 7, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(495993, 58, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdg4   ?     1001027     1001044       32672   bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1001026, 30, 55)
Partition 4 has different physical/logical endings:
     phys=(128, 0, 7) logical=(1001043, 13, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by cnbiz850 on 2008-10-08
Any ideas, Please?

---

### Post by cnbiz850 on 2008-10-10
Any help please?  At least some insights on the output of "fdisk -l" above please.

---

### Post by cnbiz850 on 2008-10-13
Hey, I guess no one would be able to help on this.  Has anyone else had this kind of experience with flash drives?

---

### Post by cnbiz850 on 2008-10-16
Still trying to figure out what is happening.

---

### Post by DraconPern on 2008-10-16
Find a friend with Windows?

---

### Post by cnbiz850 on 2008-10-18
added more info.  I think Linux definitely has some problems with these kind of devices.  Hope someone look into it.

---

### Post by cnbiz850 on 2008-10-28
Coming closer to the problems.  The most likely cause might be the removal of the .Trash-1000 folder from nautilus.  Lately, I did some file swaps and didn't see the problem occur.  The only thing different I did from before is that I did not remove the .Trash-1000 folder this time, but rather did an empty trash.

If my guess (that removing .Trash-1000 messes out the file system) is correct, then nautilus has a bug.

---

