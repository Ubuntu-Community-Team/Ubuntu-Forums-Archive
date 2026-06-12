---
title: "Errno Error everytime I try to install."
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by tjeremiah on 2009-07-10
This is driving me crazy! No matter what CD I use, I get this error and ubuntu never installs. It cant be my drive or the CD, how can this be solved?

---

### Post by tommcd on 2009-07-10
The first thing you shoud do is choose the option "Check CD for defects" when the Ubuntu CD boots up to verify that the CD is good.

How are you burning the CD? Are you burning from windows or linux? If linux, is it Ubuntu or another distro? If you are burning from windows use **Infra Recorder**.
 Whether you are burning from windows or linux, use a CDR, not a CDRW, and make sure you burn the disc at the slowest possible speed.
If all else fails, try different media. Or burn the CD from a different computer if you can.

---

### Post by jocko on 2009-07-11
> **tjeremiah said:**
> This is driving me crazy! No matter what CD I use, I get this error and ubuntu never installs. It cant be my drive or the CD, how can this be solved?
I get the same. I've burned alpha 2 and a couple of different daily images (later than alpha 2) several times to different disks at the lowest possible speed (and the disks check out ok by both brasero's built-in check and the "check cd for defects" option in the live cd boot menu), tried making bootable USB sticks, and always the same error.
With the alternate installer I instead get errors about a lot of corrupted .deb files, making the base install fail.
The same cd images work fine to install in virtualbox on my other computer.
Yesterday I noticed that after the install failed, the target partition (ext4) was mounted read-only, so I unmounted it, used gparted to delete it and then restarted the installer, now making the target partition ext3, and the install worked fine.
So there may be a hardware-specific problem that makes ext4 remount as read-only when the files are being copied to the target partition. I noticed the same behaviour when I tried to install to an ext4 partition through debootstrap (running a karmic live session), and when I come to think of it I'm pretty sure the same happened when I tried to reinstall jaunty to an ext4 partition.

Anyone have any good idea what information I need about my system to file a bug report, and what package to attach the bug to?

Tjeremiah: What computer do you have? Mine is an old nforce2 motherboard (gigabyte 7nnxp), with one normal ide controller (nforce2), one pata raid controller (ite 8212) and one sata raid controller (SiI 3112). I'm guessing the problem could be connected to the driver for one of those (the drive I've installed to is connected to the ite 8212 controller). But I guess the problem does not have to be directly connected to the disk controller...

I think I will make a couple of small ext4 partitions on both my hard drives just to see if I can isolate the problem before I submit a bug report...

---

### Post by whiteguy1104 on 2009-07-11
im having the same problem installing jaunty at 27% and im beyond frustrated. Is there anyway to tell the installer to ignore the errors or retry reading it?

---

### Post by presence1960 on 2009-07-11
see this post for your solution: [http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)

P.S. I am checking with the person who posted the solution to see if the terminal command should be > uniquity --no-migration-assistant
or > ubiquity --no-migration-assistant

---

### Post by jocko on 2009-07-12
> **presence1960 said:**
> see this post for your solution: [http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)

P.S. I am checking with the person who posted the solution to see if the terminal command should be 
or
It's ubiquity (that's the name of the live cd installer). I'll try it and report back.

---

### Post by jocko on 2009-07-12
Sadly, that did not help me. Just after the installer starts to copy files to the target partition it fails with the same error message.

So I did a quick test:
1. Created a new ext4 partition (on /dev/sdb1), checked it with e2fsck and it was ok.
2. Mounted the partition (/media/sdb1).
3. Started to copy files from another partition to the new partition.
The file copy stopped within a few seconds with a bunch of error messages like:
```
cp: cannot create directory `/media/sdb1/Led Zeppelin/led zeppelin IV': Read-only file system
```At the same time dmesg reports:
```
[  323.109900] [COLOR=Red]it821x: can't process command 0xE7[/COLOR]
[  323.109939] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  323.109952] ata5.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  323.109954]          res 50/00:fe:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  323.109959] ata5.00: status: { DRDY }
[  323.132373] ata5.00: configured for DMA
[  323.132398] ata5: EH complete
[  323.132807] it821x: can't process command 0xE7
[  323.132877] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  323.132891] ata5.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  323.132893]          res 50/00:fe:00:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[  323.132897] ata5.00: status: { DRDY }
[  323.164843] ata5.00: configured for DMA
[  323.164862] [COLOR=Red]end_request: I/O error, dev sdb, sector 117702855[/COLOR]
[  323.164883] ata5: EH complete
[  323.165075] [COLOR=Red]Aborting journal on device sdb1:8.[/COLOR]
[  323.165167] EXT4-fs error (device sdb1): ext4_journal_start_sb: [COLOR=Red]Detected aborted journal[/COLOR]
[  323.165173] EXT4-fs (sdb1): [COLOR=Red]Remounting filesystem read-only[/COLOR]
```

And after this e2fsck reports a number of errors like "the numbers of free inodes are wrong in group no 0 (8181, calculated=8167). Fix<y>?" and similar errors.
So, either my hard drive is failing and ext4 is just very sensitive to the type of errors it generates, or there is a bug in either the it821x module (the driver for my raid controller) or in the ext4 filesystem itself. I'll try to move the hard drive to the normal ata controller and try again, as well as try with an ext4 partition on my sata hard drive...

---

### Post by tommcd on 2009-07-12
> **jocko said:**
> 
Yesterday I noticed that after the install failed, the target partition (ext4) was mounted read-only, so I unmounted it, used gparted to delete it and then restarted the installer, now making the target partition ext3, and the install worked fine.

If Ubuntu installed ok on an ext3 partition then I would use that. I still use ext3. The ext4 file system in Jaunty is a bit problematic.
[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)
 This is in the kernel and is not due to the Ubuntu devs. Try ext4 again when Karminc comes out. The newer kernel in Karmic will have a better implementation of ext4.

---

### Post by jocko on 2009-07-12
> **tommcd said:**
> If Ubuntu installed ok on an ext3 partition then I would use that. I still use ext3. The ext4 file system in Jaunty is a bit problematic.
[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)
 This is in the kernel and is not due to the Ubuntu devs. Try ext4 again when Karminc comes out. The newer kernel in Karmic will have a better implementation of ext4.
Well, this *is* karmic. I'm testing it on a spare hard drive on my old computer that still has gutsy as main os. When I failed to install karmic alpha 2 I tried a jaunty cd and got the same error.

Now I've done one more test:
I inactivated the raid controller in the bios, moved the hard drive from the raid controller to the normal nforce2 pata controller, and this time installation worked flawlessly to an ext4 file system.
So the problem seems to be connected to the ite 8212 raid controller or the it821x kernel module.

I can't know if it's my hardware that's starting to give up, or if this is a bug that needs fixing, so:
[B]Is there anyone who can confirm or deny that they see massive file system corruption within seconds when they have an ext4 partition on a hard drive connected to a ite raid controller? Or any other pata/sata controller?
[/B]

---

### Post by david20 on 2009-07-12
when i try to open the cd my pc says Couldn't display "/media/Ubuntu 9.04 i386/wubi.exe". why?

---

### Post by david20 on 2009-07-12
and the cd wont start up when i turn on the pc

---

### Post by presence1960 on 2009-07-13
check your boot order settings in BIOS, make sure boot from CD is first in the order. Then if your CD still will not boot when you start your machine I would think there is a problem with the CD. If this is the case did you MD5SUM the iso image after you downloaded it. Did you burn the image to CD at the slowest possible speed (4x or 2x is perfect)? Do these things first & get back to us.

---

### Post by tommcd on 2009-07-13
> **david20 said:**
> when i try to open the cd my pc says Couldn't display "/media/Ubuntu 9.04 i386/wubi.exe". why?
What are you trying to do exactly?
Are you trying to just boot the Ubuntu live CD?
Are you trying to install Ubuntu inside Windows with **wubi**?
Please tell us exactly what you have done, and what you want to do.

To burn the Ubuntu live CD .iso to CD use **Infra Recorder** and burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot up the live CD, first choose the option "check CD for defects: and let that run. If it reports no errors, then the CD is good.
And make sure your computer's BIOS is set to boot from the cdrom drive as the first boot device, as Presence-1960 said.

And welcome to the Ubuntu forums!

---

### Post by manoa on 2010-06-27
> **jocko said:**
> [B]Is there anyone who can confirm or deny that they see massive file system corruption within seconds when they have an ext4 partition on a hard drive connected to a ite raid controller? Or any other pata/sata controller?
[/B]

the exact same error happens here too, I am not a ubuntu user (or any of the liveCD's), and I am not using a CD at all, I have some bad news and some good news: the error occurs when I am using my own compiled kernel, which happens to have these options:

the EXT4 filesystem
> Use ext4 for ext2/3 file systems

SCSI device support
> serial ATA and parallel ATA drivers
  > it 8211/2 PATA support

I don't have ext2 or ext3 enabled in kernel, kernel version is 2.6.34, however my distribution's (default) kernel does work almost fine, here's an explanation of that:

my hard drive configuration uses one hard drive per cable (at end), the 1st hard drive has only ext3, the second hard drive has ext4.

1. when both hard drives plugged in: loading default distribution kernel:
no errors, until file operations happen on/between the 1st and second hard drive (distribution kernel is same version, 2.6.34), after that errors occur, however when unmounting the 2nd hard drive (ext4) and trying to perform file operations on the 1st hard drive, **the errors still occur**.

2. when both hard drives plugged in: loading manually built kernel with the above mentioned settings:
errors occur during the system boot.

3. when only the 1st hard drive (ext3) is plugged in: loading default distribution kernel:
no errors occur (so far).

4. when only the 1st hard drive is plugged in: loading manually built kernel with the above mentioned settings:
errors occur during the system boot.

I suspect the ext4-for-ext2/3 setting takes effect in my distribution's kernel after an ext4 driver loads.

---

