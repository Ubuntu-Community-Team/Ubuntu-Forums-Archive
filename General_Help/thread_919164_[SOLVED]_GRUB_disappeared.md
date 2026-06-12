---
title: "[SOLVED] GRUB disappeared"
date: 2008-09-13
forum: General Help
---

### Post by vlvlvl on 2008-09-13
I have had XP and Ubuntu on my HP laptop for some time. 
After installing a HP 1300 Series printer and removing some unwanted parts of the HP printer software today, the boot choice disappeared and only Windows can be started. 
The disk management of Windows says the Linux partition is sound.
What to do?

---

### Post by caljohnsmith on 2008-09-13
Boot your Live CD, open a terminal, and try the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be all it takes, but let me know how it goes or if you run into other problems.

---

### Post by xenolalia on 2008-09-13
Hi!

I once had a similar problem.  Try a tool called Super Grub Disk (very useful in fixing disappearing grub menus).

Here's a link:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You might also look at this ubuntu tutorial (I know it doesn't completely apply to you, but I have a feeling that your problem is similar . . . ):

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Good luck!

---

### Post by vlvlvl on 2008-09-14
Thank you for the advice. Now I have Grub, slightly different from the previous one, but still have a seemingly serious problem, see attached photo of the received screen. Bye VL


> **caljohnsmith said:**
> Boot your Live CD, open a terminal, and try the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be all it takes, but let me know how it goes or if you run into other problems.

---

### Post by vlvlvl on 2008-09-14
Thank you, I tried the SuperGrubDisk but somehow could not manage to fix the HD.
Grub came only with the disk inserted, but the system did not start.

---

### Post by caljohnsmith on 2008-09-14
So are you getting that fsck error when you try and boot Ubuntu from the Grub menu? If so, I would boot your Live CD, do the following:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo fsck -y /dev/sdXY
```
After it is done, reboot, and see if you can boot Ubuntu. Let me know how it goes or what errors you get.

---

### Post by vlvlvl on 2008-09-15
Hi 
I received the following screen on the terminal (I guess the partition table is ok,):

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1bba1bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30723839    15361888+   7  HPFS/NTFS
/dev/sda2        30723902   193475519    81375809    f  W95 Ext'd (LBA)
/dev/sda3       193475520   213947999    10236240    c  W95 FAT32 (LBA)
/dev/sda4       213953670   234435599    10240965   83  Linux
/dev/sda5        30723903    61447679    15361888+   7  HPFS/NTFS
/dev/sda6        61447743   193475519    66013888+   7  HPFS/NTFS


ubuntu@ubuntu:~$ sudo fsck -y /dev/sda4
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
The filesystem size (according to the superblock) is 2560359 blocks
The physical size of the device is 2560241 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

ubuntu@ubuntu:~$

After restart I ended up here (see screenshot).

---

### Post by caljohnsmith on 2008-09-15
When you restart and get dropped into the command prompt:
```
root@v1-laptop:~#
```
Just do: 
```
fsck -y /dev/sda4
```
Be sure to let it proceed (don't abort it this time). Let me know the results and we'll work from there.

---

### Post by vlvlvl on 2008-09-15
Hi,
Abort(? and "yes") and the command line come without touching a key, like this:

Either the superblock or the partition table is likely to be corrupt!
Abort? yes

ubuntu@ubuntu:~$






> **caljohnsmith said:**
> When you restart and get dropped into the command prompt:
```
root@v1-laptop:~#
```
Just do: 
```
fsck -y /dev/sda4
```
Be sure to let it proceed (don't abort it this time). Let me know the results and we'll work from there.

---

### Post by caljohnsmith on 2008-09-15
OK, when it says "Abort? yes", can you delete the yes, type "no", press return, and have it continue?

---

### Post by vlvlvl on 2008-09-15
Not possible, I can only type in the next command line.

---

### Post by caljohnsmith on 2008-09-15
OK, let's check your partition table; from the Live CD, do:
```
sudo apt-get install testdisk

```
You'll need an internet connection to install the testdisk package. Then do:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. If it returns any errors, proceed with a deeper scan by choosing "proceed", "N" to find Vista partitions, hit enter and select "search!" so it does a deeper search, which will take a while. Please post the output of that screen once it is done.

---

### Post by vlvlvl on 2008-09-16
Net is on. Message: Testdisk package cannot be found.
Interesting:
By means of the Paragon HD Manager (Win based) even files of the EXT partition can be seen (see attachments).

---

### Post by caljohnsmith on 2008-09-16
OK, go to System > Preferences > Software Sources, and make sure all the repositories are enabled. Then try to install and use testdisk again.

---

### Post by vlvlvl on 2008-09-17
To my astonishment my original Ubuntu system started, I installed testdisk and did the search. Results attached. I wonder if it starts again next time.

---

### Post by vlvlvl on 2008-09-17
Unfortunately Ubuntu started only once, I inserted the livedisk only after grub started, but could not repeat it. Now the same errors as earlier.

---

### Post by Jonie on 2008-09-17
I would not mess with the partitions using testdisk. It just reports different geometry was used when Windows partitions were created - by changing this you will invalidate FAT/NTFS boot sectors and you'll no longer be able to boot Windows.

You can restore superblock from backup, it may have been damaged by power / battery failure.

```
sudo dumpe2fs /dev/sda4
```


This will give you detailed information about the filesystem.
Notice the block size and superblock backup locations.

Then try to mount the filesystem from a LiveCD using backup superblock:

Let's assume that the block size is 4k and first superblock backup is located in the block 32768.

```
sudo mount -t ext2 -o sb=_131072_ /dev/sda4 /mnt/sda4
```

where _this value_ of 131072 is derived from superblock bakup location 32768 * block size 4 (kilobytes).

If it doesn't complain in any other other way than warning you that you mount ext3 as ext2, so far so good. Else you may try other superblock backups using the same formula.

Then _umount /dev/sda4_ (mandatory before proceeding!)

```
sudo e2fsck -b 32768 /dev/sda4
```

Now the issue should be fixed.

---

### Post by vlvlvl on 2008-09-18
See dump in the attachments. Now I do not know where (and which) are superblock backups and block sizes. Thanks in advance for some explanation. VL

---

### Post by caljohnsmith on 2008-09-18
In those attachments you posted there is no mention of any backup superblocks for your Linux partition. Try the following just to be sure:
```
sudo dumpe2fs /dev/sda4 | grep superblock
```

---

### Post by Jonie on 2008-09-18
I discovered something interesting:

First, read this post:

[http://ubuntuforums.org/showthread.php?t=879932]("http://ubuntuforums.org/showthread.php?t=879932")

then...

The difference between device size and the size reported by superblock is 944 when converted to sectors, add one (for superblock) and you've got 945.

945 is 15 * 63 = difference in geometry.

sda4 doesn't end on cylinder boundary either when calculated with cylinders of 255 heads nor with 240 heads. It has 1274 cylinders of 255 heads + one of 240 heads.

vlvlvl's BIOS reports 240 heads, Linux sees 255. The size coded in the superblock is that including partial last cylinder, fsck reports the size in cylinders of 255, thus wthout it.

It's possible, that Super GRUB shrunk the device by 15 heads and borked the filesystem. If so, we have to recreate the partition using CLI parted and add the missing 15 heads at the end. Restoring superblock will do nothing, it seems I've chosen wrong path before.

---

### Post by vlvlvl on 2008-09-19
My computer is a HP-Compaq laptop, and also the earlier error messages indicate the problem of 240 vs 255 heads. How to restore 255 for Linux?

---

### Post by vlvlvl on 2008-09-19
What if I reinstall Ubuntu? Settings and installed progs will be lost?

---

### Post by Jonie on 2008-09-19
First of all, the difference is not random, I'm affraid, wasn't it for that you'd have an easy fix by restoring the superblock.
If you read the link, you'll see that  there's nothing wrong with the BIOS going its own way and Linux its own, too.

You may try to recreate the last (Linux partition)

sudo parted

rm 4 // this removes the Linux partition)

mkpart primary ext3 213953670s 234436544s

// creates a partition with the same beginning cylinder and ending exactly at the last whole cylinder using geometry of 255 heads)
// make no mistake when typing those numbers!
// don't replace by any means mkpart with mkpartfs, the latter would delete all data from the partition!

quit

If something goes wrong, please write.

---

### Post by vlvlvl on 2008-09-19
Hi, 
Is it quite sure? I got the data in sda4.txt and sda4-1.txt using the liveCD. Does the liveCD recognise the Linux partition also as sda4 like the installed Ubuntu? What about a repeated installation to the same partition?

---

### Post by caljohnsmith on 2008-09-19
> **Jonie said:**
> I discovered something interesting:

First, read this post:

[http://ubuntuforums.org/showthread.php?t=879932]("http://ubuntuforums.org/showthread.php?t=879932")

then...

The difference between device size and the size reported by superblock is 944 when converted to sectors, add one (for superblock) and you've got 945.

945 is 15 * 63 = difference in geometry.

sda4 doesn't end on cylinder boundary either when calculated with cylinders of 255 heads nor with 240 heads. It has 1274 cylinders of 255 heads + one of 240 heads.

vlvlvl's BIOS reports 240 heads, Linux sees 255. The size coded in the superblock is that including partial last cylinder, fsck reports the size in cylinders of 255, thus wthout it.

It's possible, that Super GRUB shrunk the device by 15 heads and borked the filesystem. If so, we have to recreate the partition using CLI parted and add the missing 15 heads at the end. Restoring superblock will do nothing, it seems I've chosen wrong path before.
That is interesting info, Jonie; thanks for sharing it. I wasn't aware that the Linux partitions could have a different cylinder geometry then the Windows paritions; I was under the impression that the entire HDD had to use the same cylinder geometry for all partitions. And to add to my confusion, I noticed in testdisk, if you go to the "Geometry" screen, it will let you change the cylinder setting, but not for individual partitions it looks like--only for the entire drive. 

Another thing I'm confused about: you say above that "sda4 doesn't end on cylinder boundary either when calculated with cylinders of 255 heads nor with 240 heads", but is ending on a cylinder boundary necessary? I thought that partitions only have to end on sector boundaries, not necessarily cylinder boundaries. I could give some examples of people in the forums who had partitions that didn't land on the cylinder boundaries, but as long as their partitions didn't overlap at the sector level, then testdisk was happy and said their partition structure was fine.

What are the implications then of that link you posted above? Would that mean you can't use testdisk to recover a partition structure where different partitions use different cylinder geometries? If so, that would mean just about every HDD that first had Windows on it and then was partitioned into a dual-boot system. I've never delved into this level of technical details for HDDs nor when using testdisk, so I certainly don't know. Any more thoughts on all this, Jonie? :)

---

### Post by Jonie on 2008-09-19
@caljohnsmith:

> Another thing I'm confused about: you say above that "sda4 doesn't end on cylinder boundary either when calculated with cylinders of 255 heads nor with 240 heads", but is ending on a cylinder boundary necessary?

That's very good question. It isn't mandatory, but more than recommended. A whole lot of software uses it as a workaround for not-so-reliable BIOS geometry. Geometry is calculated then the other way round, from the partition table. The only exception which is entirely allowed is for loop devices (floppies, ZIPs, unMBR'ed thumbdrives and so on), but this is really not an exception since such devices have no geometry at all, just the raw size. A rule of thumb is that "the geometry" in the partition table should match one that given OS sees and that the partitions don't overlap in a physical way i.e. they share no single sector.

The case in this tread is a good example. Windows relies on BIOS, it sets geometry of 240 and it's quite happy about it. Any legacy code there might be would calculate the geometry backwards, good, there is 240. Linux does not rely on BIOS. It just expects 255 heads, and for any consistency check there's got to be such multiple of sectors. As you can see, superblock holds the filesystem size as a multiple of cylinders of 255 heads. I suspect some commercial software that broke the device size. I once ran into breakage using BSD partitioner (not commercial, but not GPL ;) on a disk setup as LRG (240 heads).

> What are the implications then of that link you posted above? Would that mean you can't use testdisk to recover a partition structure where different partitions use different cylinder geometries? If so, that would mean just about every HDD that first had Windows on it and then was partitioned into a dual-boot system.

240 heads geometry called also Large (LRG) is a workaround for legacy systems as DOS, few older branded laptops use it, you may select it also manually in most of the dektop BIOSes. 255 heads is the standard now and this is a rare exception. Thumbdrive manufacturers often violate this standard in order to make available as much capacity as advertised.

vlvlvl's partition size looks as if it were cut at 239th cylinder, but using geometry of 255

@vlvlvl:

I don't think Linux would set the partition size you reported. It looks very much that its size is screwed. You should change it as I wrote before. As long as you've got one disk, yes, sda4 will stay sda4 no matter how the system is started. If you reinstall system to the partition as it is now, it might work... until you run into another breakage. The fix I suggest is just to add a bunch of otherwise totally empty sectors at the end of the disk, to satisfy fsck and it would be probably better than to force superblock into the weird device size. It's rather safe as long as you understand it and make no mistake. If there's anything unclear we're here for the asking ;)

---

### Post by vlvlvl on 2008-09-22
Hi Jonie, I was away for some days, but noe I carried our the partition modification and IT WORKED!!!! 
tHANKS FOR THE ADVISES AND ALSO THANKS FOR THE CONTRIBUTIONS TO CALJOHNSMITH!

---

### Post by Jonie on 2008-09-22
You're welcome. Please mark the thread as solved.

---

