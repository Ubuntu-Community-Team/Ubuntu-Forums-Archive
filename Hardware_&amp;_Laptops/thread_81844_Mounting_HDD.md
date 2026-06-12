---
title: "Mounting HDD"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by iam10ninjas on 2005-10-25
I have a Gigabyte board with GigaRAID onboard. I have a HDD attached to one of the IDE ports, so I effectively have 3 IDE drives connected to the board:

[list]
[*]hda1 = windows XP drive
[*]hdb1 = Unbuntu drive
[*]Third drive with data.
[/list]

I tried finding the drive in /etc/fstab in both RAID and IDE configurations (by changing the option in the BIOS) and came up empty on both counts.

I have manged to mount my WinXP drive, and it appears on my desktop, along with my USB thumbdrive.

Does anyone have any advice as to how I go about finding this drive?

Thanks in advance.

P.S. This is my first foray into Linux, and I am loving Ubuntu.

---

### Post by iam10ninjas on 2005-10-25
I have since discovered that the drive I installed Ubuntu on has two partitions:

[list]
[*] /dev/hdb1. ext3 file system. Access Path: /boot (this is accessible)
[*] /dev/hdb5. unformatted. Access Path: none (unaccessible and I cannot enable it from Disks Manager)
[/list]

This is really starting to bug me now. I've looked high and low for a solution, and nothing seems to be forthcoming.


*shakes fist in the air*

---

### Post by iam10ninjas on 2005-10-26
Thanks for all your help guys...

:rolleyes:

---

### Post by iam10ninjas on 2005-10-31
Ok. I have since re-installed Breezy and sorted out the partitions.

Here is fstab output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda1	/media/windows	ntfs	nls=utf8,umask=0222	0	0

To get around the problem of not being able to access the drive I mentioned previously (the disk with all the data on it) by putting it in a portable HDD caddy and running it as a USB device.

I tried to recompile the kernel with the ITE RAID drivers included, but failed miserably, and gave up with that because I doubt it would have made any difference.

Does anyone have any othe ideas as to how I can have this data disk mounted in Breezy *without* having to use it as a USB device, as all my apps that run in WinXP are on there, and I often need to run CAD and DTP progs. I don't want the hassle of shutting down the comp, taking the disk out of the caddy, putting it back onto the IDE channel and rebooting into XP, then reversing the process to use Breezy again.

I really. really don't want this to be the reason I stop using Ubuntu, because I have discovered how stable my PC can actually be.

HW Specs:

Athlon XP3000
Gigabyte GA-&N400 Pro2 (this seems to be the problem, with the HW RAID)
1 Gig RAM
GeForce FX 5200

---

### Post by Rouge8 on 2005-10-31
I know this might seem rather basic, but did you try 'sudo fdisk -l' ?

---

### Post by iam10ninjas on 2005-11-01
This is the output of 'sudo fdisk -l'

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2330    18715693+  83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/sda: 1048 MB, 1048576000 bytes
1 heads, 32 sectors/track, 64000 cylinders
Units = cylinders of 32 * 512 = 16384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       64000     1023984    b  W95 FAT32

---

### Post by Rouge8 on 2005-11-01
I assume it's not the 1048 MB drive, but that means Ubuntu isn't detecting it at all. I dunno. Maybe check the motherboard manufactorer's site to see if they have any drivers? Also try the linux google or even a forum search if you haven't.

Other than that, I'm not sure what to do, sorry.

---

### Post by iam10ninjas on 2005-11-02
I have a funny feeling its due to the ITE RAID drivers not being supported in Breezy.

I have read numerous threads about recompling the kernel with an ac-patchset, but the kernel they are talking about is older than the one I'm currently using, so I don't see how this would help.

Unless I compile the current one with the ITE drivers included, but I'm not overly confident in this being a workable solution. I'm gonna give up for now and wait to see if someone comes up with a more workable solution.

Thanks for taking the time to reply, Rouge. I appreciate it.

---

### Post by iam10ninjas on 2005-11-29
The recent kernel update has added some functionality to the other IDE ports and I think DMRaid has been fully activated somehow.

The new problem is that the 3rd HDD is being detected as a CD-Rom drive with the label "/dev/hdd" which is what it should be, based on the other drive designations. The drive has 3 partitions, and editing fstab with what I hope are the correct entries yeilds nothing. (hdd1 - hdd3 being the partitions and the filesystem being ntfs.)

All this means is that I cannot mount it. Hopefully it isn't hosed.

Any ideas guys?

---

