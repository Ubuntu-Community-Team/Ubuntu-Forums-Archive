---
title: "Cannot mount NTFS partition"
date: 2005-11-23
forum: General Help
---

### Post by thejon on 2005-11-23
I have a 200 gig drive partitioned into 3 parts. One with a windows install one with a linux install, and one for shared data use. I'm going to note that I am very new to the linux stuff but I'm getting very fed up with MS. Any how I go to "filesystem" "dev" and not even in there do i find any sign of my other partitions, I've tried using the # usermount & but that does not get me anywhere. I've also tried using the other mounting procedure but that just bumps me to a new terminal line and does nothing. Can anyone help me out here? My 25 gigs of music is craving Ubuntu!

Thanks,
Jon

---

### Post by xmastree on 2005-11-23
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
That's the guide for 5.04 but it will work the same with 5.10

Edit: I should also add that you will only be able to read that partition, not write to it. If you wish to share a writeable partition between the two, it's best to use FAT32.

---

### Post by aysiu on 2005-11-23
You say you have one for shared use? I hope that's not the NTFS partition because NTFS is read-only in Linux.

In any case, everything you need to know is here:

1. **Where do you type command people give you?** Applications > Accessories > Terminal

2. **Where are your partitions?** Type this in a terminal ```
sudo fdisk -l
```

3. **How do you mount the partitions?** [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

4. **How do you get the changes to take effect?** Reboot or ```
sudo mount -a
``` I prefer reboot, but it takes longer... obviously.

---

### Post by thejon on 2005-11-23
Yes the shared partition is NTFS, however I wouldn't mind formatting it and converting it to fat32. But I just dont know how to do that...

Would anyone be able to shed the light?

JON

---

### Post by xmastree on 2005-11-23
[http://www.ubuntuforums.org/search.php?searchid=2642906](http://www.ubuntuforums.org/search.php?searchid=2642906)

[http://www.ubuntuforums.org/showthread.php?t=90676&highlight=convert+ntfs+FAT32](http://www.ubuntuforums.org/showthread.php?t=90676&highlight=convert+ntfs+FAT32)

---

### Post by thejon on 2005-11-24
Alright, so I booted into windows and pulled everything off of the "shared" drive thinking i could format it in Fat32 in windows but it only gives me the NTFS option. I then booted into Ubuntu and went into System > Administration > Disks and tried using the Vfat32 format which it took about 4 seconds to do and it still says "inaccessable" I clicked enable and all hell broke loose (so it appeared) both the menu and window panels dissapeared.

My only option was to hit the restart button.

Any ideas?

Oh and happy thanksgiving everyone...

---

### Post by WebDrake on 2005-11-24
[QUOTE=thejon]Alright, so I booted into windows and pulled everything off of the "shared" drive thinking i could format it in Fat32 in windows but it only gives me the NTFS option.[/QUOTE]

How big is the partition you want to format?  FAT32 can only really cope with up to 32GB.

IMO we badly need a filesystem dedicated to read/write access from both Windows and Linux, that does not have these sort of size limitations and that *does* work effectively.  There is a driver allowing ext2/ext3 read/write access from Windows but apparently it's not stable in the long run if you're going to be doing a lot of writing from Windows.

(... This opinion was formed after a lot of time spent today buggering around trying to set up an 80GB USB drive for use with both operating systems. ;-) )

---

### Post by thejon on 2005-11-24
Well I suppose that could be partly the problem the partition size is 63.31Gig's. Should i split this into two partitions? and how would i do so. Or does anyone have a better Idea what to do?

---

### Post by aysiu on 2005-11-24
[QUOTE=WebDrake]How big is the partition you want to format?  FAT32 can only really cope with up to 32GB.[/QUOTE] My FAT32 partition is 100 GB and works just fine: ```
sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       18494   133202947+   f  W95 Ext'd (LBA)
/dev/hda3           18495       19457     7735297+  83  Linux
**/dev/hda5            1912       14763   103233658+   b  W95 FAT32**
/dev/hda6   *       14764       16434    13422276   83  Linux
/dev/hda7           18363       18494     1060258+  82  Linux swap / Solaris
/dev/hda8           16435       18362    15486628+  83  Linux

Partition table entries are not in disk order
``` The size limitation in FAT32 is on the files within the partition, not the partition itself. I think it's something like 4 GB or 6 GB--it cannot handle *files* that are bigger than that. Personally, and I don't have backups of DVD movies or anything, the largest files I have are about 7 **M**B (not **G**B).

[quote=thejon]I then booted into Ubuntu and went into System > Administration > Disks and tried using the Vfat32 format which it took about 4 seconds to do and it still says "inaccessable" I clicked enable and all hell broke loose (so it appeared) both the menu and window panels dissapeared.[/quote] Make sure the partition is unmounted before trying to reformat it. To reformat it, use something like GParted (you can find it in the repositories). Then, follow [these instructions](http://www.ubuntuguide.org/#automountfat) to get the FAT32 partition properly mounted.

---

### Post by thejon on 2005-11-24
Gparted you said can be found in the repositories... how do I get to this, remember I'm very new to Linux. Is this software I can download and install or is it basic utility i can get to through a terminal session?

---

### Post by aysiu on 2005-11-24
Open up a terminal (Applications > Accessories > Terminal) and type these commands in ```
sudo apt-get update
sudo apt-get install gparted
``` You'll be prompted for your password. Enter it. Then, after that, Gparted should be installed and ready to use.

There's a graphical way to do this, as well. If you'd rather do it that way, check out the second link in my sig.

---

### Post by thejon on 2005-11-24
I crack myself up... stupidly i was messing around with Gparted and formated the entire hard drive! OOPS!

thankfully i've got everything backed up to my external drive. What I did this time was install windows first and partition it with NTFS then left the rest of the drive unpartitioned. Once windows was finished installing I installed Ubuntu and used its partitioner to setup one partition with EXT and the other with FAT32. Now Ubuntu is mounting to the NTFS partition and as according to Disk Manager its also mounting the FAT32 partition as well, but the NTFS partition appears on my desktop as a drive and the FAT32 partition is a folder in my "filesystem" directory. Why doesn't it show as another drive?

---

### Post by WebDrake on 2005-11-27
[QUOTE=aysiu]My FAT32 partition is 100 GB and works just fine: ...

The size limitation in FAT32 is on the files within the partition, not the partition itself. I think it's something like 4 GB or 6 GB--it cannot handle *files* that are bigger than that. Personally, and I don't have backups of DVD movies or anything, the largest files I have are about 7 **M**B (not **G**B).[/quote]

That's what I had thought too; but I had a hell of a time trying to format my 80GB USB hard drive with FAT32.  Eventually I just decided to create 3 partitions, 32+32+remainder.  Windows XP (current full-time OS, but I'm working on it...) wouldn't let me format the full disk in anything under than NTFS, and I couldn't work out how to do so with FAT32 with the Ubuntu Live CD either. :-( 

Obviously I'm wrong, but I got the impression from various things I've read that although it's *possible* to work with larger FAT32 partitions, it's *easier* to work with smaller ones.  Hence above misleading comment... :rolleyes:

---

### Post by ninocass on 2005-11-27
sorry for posting in the middle of the topic but i feel the question doesnt warrent another "NTFS partition" thread.  I have managed to get my drives to mount but when i restart the drive is gone.

Thanks

Nino

---

### Post by aysiu on 2005-11-27
[QUOTE=ninocass]sorry for posting in the middle of the topic but i feel the question doesnt warrent another "NTFS partition" thread.  I have managed to get my drives to mount but when i restart the drive is gone.

Thanks

Nino[/QUOTE] Read [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

You can manually mount partitions.
And you can have them automatically mount on boot-up.
Those instructions are for automatic mounting.

---

### Post by ninocass on 2005-11-27
working a treat!!

many thanks

Nino

---

### Post by lanceh on 2005-11-30
[QUOTE=WebDrake]That's what I had thought too; but I had a hell of a time trying to format my 80GB USB hard drive with FAT32.  Eventually I just decided to create 3 partitions, 32+32+remainder.  Windows XP (current full-time OS, but I'm working on it...) wouldn't let me format the full disk in anything under than NTFS, and I couldn't work out how to do so with FAT32 with the Ubuntu Live CD either. :-( 

Obviously I'm wrong, but I got the impression from various things I've read that although it's *possible* to work with larger FAT32 partitions, it's *easier* to work with smaller ones.  Hence above misleading comment... :rolleyes:[/QUOTE]

The problem is that windows NT/2000/XP will not create a FAT32 partition larger than 32GB. This is done to force people into using NTFS. If you can get the partition formatted by another means (linux, gdisk, etc.) windows can work with it fine.

---

