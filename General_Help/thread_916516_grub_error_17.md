---
title: "grub error 17"
date: 2008-09-11
forum: General Help
---

### Post by umarali on 2008-09-11
i have (or had :/) feisty installed on my machine...it would give me sum problems occasionally, but running fsck wud fix that.
HOWEVER!! last nite, while i was doing my usual, sufring + listening to music + k torrent running in the background, routine...it suddenly just froze.
so i restarted it
and it wouldn't boot now!!
it goes like:
"loading GRUB

GRUB error
ERROR 17 "

i dun have dual booting or anything!
WHAT DO I DO???
i have important data on that machine!!!! :/ :(
any help would be greatly appreciated!!!

---

### Post by mrsteveman1 on 2008-09-11
Easiest thing would be to grab the super grub CD which can fix it automatically (this should be part of the ubuntu cd).

---

### Post by umarali on 2008-09-11
so.......do i just put in the feisty cd... :S
sorry...im kinda new.. :/

---

### Post by caljohnsmith on 2008-09-11
Most likely the cause of your Grub error 17 is that Grub can no longer read from your Ubuntu partition since Ubuntu was shutdown improperly. Probably all you need to do to fix it will be to run fsck on it. Just boot your Live CD, open a terminal, and if you don't know which is your Ubuntu partition, first do:
```
sudo fdisk -l
```
Look for the partition that is type "linux" under the "system" category, and then run fsck on it:
```
sudo fsck /dev/sdaX
```
Of course replace sdaX with your Ubuntu partition. Let me know how it goes or if you run into further problems.

---

### Post by umarali on 2008-09-15
sorry for this really late reply...was unable to get internet access!
so i tried that.....
the thing is...ive the live cd for 7.04...and when i did that i said that no command exists: sudo fsck/....
and cuz of only got a single drive...(dint make any partitions)....i thought maybe i should also try with just simply fsck
i did that too....an all it said was:
"fsck 1.40-WIP (14 nov-2006)"
and moved to the next line
nothing happened!!!!!
:/

---

### Post by umarali on 2008-09-18
hello?
:/

---

### Post by umarali on 2008-10-07
!!!!!!!!!
come on people!!!!!

---

### Post by go_dragons on 2008-10-07
Hey man,

Grub error 17 occurs when the partition information stored in grub are different than the ones actually on the disk. This can mean that either your partitions are messed up, OR that your MBR is actually messed up.

I dont think fsck will help you because fsck fixes the actual filesystem on the partition, not the partition itself. 

Try booting into a live CD and using fdisk -l to find out if your partitions are correct. Here is an example of what mine looks like:

```
bash-3.2# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015390

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        1714    13671315   83  Linux
/dev/sda4            1715       30401   230428327+  8e  Linux LVM
```

If yours looks similar to this, then your partitions are correct.
you can further verify that your partitions are correct if you go into a live cd and you can chroot into the drive. type 
```
sudo mkdir /some/directory
sudo mount /dev/sda1 /some/directory
sudo chroot /some/directory
``` 
and if you dont get errors then all is well on the partition front and you know that your problem is actually on the MBR.
explanation - chroot does a 'change root' so within that terminal window it is acting as if the root directory is on /dev/sda1 instead of the root of the CD. You can navigate the hard drive now the same as you would if you had booted from the hard drive.

If all of that worked fine then I think you can assume the problem is on the MBR. This is what I recommend: try just reinstalling grub onto the drive.
you do this by issuing grub-install like this:

```
sudo grub-install /dev/sda
```
(notice I said sda not sda1. Of course yours might be hda depending on your system)
What this does is it loads grub back onto the MBR so it should erase whatever corruption is currently in place.



these two sites might be helpful if that doesn't work:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
[http://hertenberger.co.za/?p=808](http://hertenberger.co.za/?p=808)

---

### Post by gandalf2000 on 2008-10-08
I have been struggling with the same problem for the past few days and finally found the answer here on the forums.  For my problem it was in the BIOS, the boot up order of the hard disk drives was wrong.  Once I corrected that I got my boots back.

---

