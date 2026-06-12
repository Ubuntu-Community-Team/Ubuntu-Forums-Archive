---
title: "SD card rarely mounts, when it does its write protected :("
date: 2009-06-06
forum: Hardware
---

### Post by theyain on 2009-06-06
I have an SD card that I use to listen to my music on my crappy MP3 player.  Recently I formatted it to ext3 just to play around.  But lately I can't seem to get the system to be able to mount the card.  When I try to mount it I get this error
```

theyain@theyain-laptop:~$ sudo mount -t ext3 /dev/mmcblk0 /media/disk-2
mount: block device /dev/mmcblk0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Doing dmesg | tail gives me

```

[ 3766.056355] EXT3-fs error (device mmcblk0): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 3766.056365] EXT3-fs: group descriptors corrupted!
[ 3877.393180] tifm0 : demand removing card from socket 0:3
[ 3877.393230] mmc3: card ea0d removed
[ 3880.868037] tifm_core: MMC/SD card detected in socket 0:3
[ 3881.043815] mmc3: new SD card at address ea0d
[ 3881.066806] mmcblk0: mmc3:ea0d SD01G 968 MiB (ro)
[ 3881.066896]  mmcblk0: unknown partition table
[ 3881.439400] EXT3-fs error (device mmcblk0): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 3881.439411] EXT3-fs: group descriptors corrupted!

```

The odd thing is that less then 10 minutes ago I was able to mount it and delete all the information on it.

When I try to fsck the system, I get this

```

fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/mmcblk0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

The command at the end gives me the same thing. But thats because for some reason the card is write protected.  Yes, I already checked to see if its physically in lock mode, it is not.  I've also tried reading it when its locked, still no dice.  Any clue anyone?

---

### Post by aysiu on 2009-06-07
Maybe *testdisk* might help?

[http://www.linuxquestions.org/questions/linux-hardware-18/bad-magic-number-in-super-block-while-trying-to-open-devhda6-503291/](http://www.linuxquestions.org/questions/linux-hardware-18/bad-magic-number-in-super-block-while-trying-to-open-devhda6-503291/)

---

### Post by theyain on 2009-06-07
What an awesome program.

I was able to fix the problem :D

---

### Post by theyain on 2009-06-07
Okay, now it's saying its in read-only mode.  I know its not physically set to RO mode, so I'm still stumped.

I ran testdisk on it again to see what I could find and some of the superblocks are now fat32, while others are ext3.


At the very least I'm able to mount it now.  However (as I previously stated) I can't write to it.  Whats really odd is that earlier/immediately after I ran testdisk on it for the first time, I was able to format it to fat32.  But now gparted is showing that it's just unallocated space and I can't format it.

Hmm, now I have a new symptom thats utterly perplexing.  I just switched the physical tab to lock mode... and now I can write to the card, but only as root.

---

### Post by theyain on 2009-06-08
Bump

---

### Post by Gasen on 2010-10-04
This is kind of an old post, but no one should have to wait weeks like I did to find a solution. First double check the physical lock on the card.

If you haven't done it already, use TestDisk to backup the data on your SD card. Your going to need to format your card. Once you format it, it should mount automaticly and not be write protected. 

[http://ubuntuforums.org/showthread.php?t=208980]("http://ubuntuforums.org/showthread.php?t=208980")

> Insert your memory card,

Open a terminal and type: df

df will tell you the device name of your memory card, in my case it was /dev/sdb1

unmount the disk

then just type: mkdosfs /dev/sdb1

mount it back (i just replugged it)

And I agree, TestDisk is an awesome program. I got data back, that I thought was lost forever. [http://www.penguintutor.com/blog/viewblog.php?blog=2178]("http://www.penguintutor.com/blog/viewblog.php?blog=2178")

---

