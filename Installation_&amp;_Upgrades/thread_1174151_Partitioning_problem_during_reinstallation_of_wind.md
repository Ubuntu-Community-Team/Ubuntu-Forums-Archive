---
title: "Partitioning problem during reinstallation of windows on ex-Ubuntu partition"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Salmontarre on 2009-05-30
Hello.

I'm having quite the problem.  I am shipping this computer off to my sister, and she refuses to use Ubuntu, so I'm putting windows back on it before she takes it.

It has a 320gb hard drive, split into two partitions.  Originally, it was running windows, but some time ago I nyxed windows, installed Ubuntu on the smaller partition using ext3, and kept the larger partition with all the personal data intact as a NTFS partition.

Now I want to put WinXP back on the smaller partition.

Booted from CD, deleted the small swap partition Ubuntu uses, formatted that and the Ubuntu install partition into NTFS, which should have left me with two NTFS partitions, the large, backup partition never being touched.  Install windows, blah blah.

Reboot, and nothing happens.  After the device listing, there is no GRUB errors, just a blinking cursor (can't type anything, ofc).

So I boot into this 8.10 LiveCD, and, assuming it's a MBR problem, I type in: 

```
ubuntu@ubuntu:~$ sudo apt-get install mbr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mbr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo install-mbr -i n -p D -t 0 /dev/sda
ubuntu@ubuntu:~$ 

```

Reset, same problem.

I try fixmbr from Windows recovery, which, by the way, boots me into D:/Windows... what?  It should be C:/Windows, I thought.  So I go back into LiveCD, and do:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   102398309    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *   102398373   625121279   261361453+   7  HPFS/NTFS
/dev/sda5           16128   102398309    51191091    7  HPFS/NTFS

```

This is where I get lost.  Are those Start/Ends messed up?  Shouldn't the boot be on sda5, which is the smaller partition?  I don't even know what sda1 is.

I also ran the bootinfoscript, in case it helps anyone figure this out.  Here is the output:

```
============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 102398373.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   102,398,309   102,382,245   f W95 Ext d (LBA)
/dev/sda5              16,128   102,398,309   102,382,182   7 HPFS/NTFS
/dev/sda2    *    102,398,373   625,121,279   522,722,907   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="9464D33964D31D34" TYPE="ntfs" 
/dev/sda5: UUID="04A03FF9A03FF032" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

Those mounting fail messages are what I get when I try to look at the contents of the partitions from the LiveCD GUI, as well.

Any help would be great, I'm at a total loss for how to fix this.  I'll watch thread closely, so if you need more information please ask!

---

### Post by merlinus on 2009-05-30
From what I can see, sda1 is an extended partition which contains the two logical partitions sda2 and sda5.  Since sda2 has a boot flag, it is probably your xp installation.

What is interesting, however, is that sda5 precedes sda2 on your hdd.  The partition numbers probably got messed up with all the changes.

The supergrub disk should allow you to boot into xp, and even restore the mbr.

---

### Post by Salmontarre on 2009-05-30
Hmmm.

I thought that sda2 was my large, permanent partition (music, documents, backups and such), and that sda5 was where my windows install must have ended up.

For clarity, since maybe I worded it funny, when I booted from the windows CD for the first time, it showed me the 4 partitions: big one, ubuntu install, ubuntu swap, and 8mb leftovers.

What I did was to delete the swap partition, delete the ubuntu install partition, and format all that into a new NTFS, then I installed to it.

The weird part is that when I do fdisk -l, sda1 and sda5 have the same start and end:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff0bff0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *        6375       38912   261361453+   7  HPFS/NTFS
/dev/sda5               2        6374    51191091    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

Should I just format sda1 and sda5 again?  If so, how should I go about doing that?

---

### Post by Salmontarre on 2009-05-30
Hmm, weird.  I don't think I've done anything that I haven't typed, but I can now mount and view contents of two partitions from this LiveCD environment.

I have a 267.6gb partition which contains my backups.

And I have a 52,4gb partition with the windows folder and such.

Edit:  Just reran the boot info script --

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  [B]According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 102398373.[/B]
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff0bff0b

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   102,398,309   102,382,245   f W95 Ext d (LBA)
/dev/sda5              16,128   102,398,309   102,382,182   7 HPFS/NTFS
/dev/sda2    *    102,398,373   625,121,279   522,722,907   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="9464D33964D31D34" TYPE="ntfs" 
/dev/sda5: UUID="04A03FF9A03FF032" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by merlinus on 2009-05-30
Weird is right!  So your primary partition is the big one, and then you have an extended partition (sda2) which contains xp (sda5).  Can you boot into xp, because usually it wants not only to be in a primary partition but also in the first one on the hdd?

---

### Post by Salmontarre on 2009-05-30
I'll go try, right now :)

---

### Post by Salmontarre on 2009-05-30
Nah, same deal.  After listing PCI devices, it just sits there.

I went into windows recovery again, and it takes me to D:/Windows.  I can go to the C:, and yeah, that's where my backup partition is hanging out.

Is there a way to simply rename the partitions?

---

### Post by merlinus on 2009-05-30
Don't think so, because even renaming would not change the fact that xp is not in a primary partition that is first.  You might do best to back up important data and start over.

You might try editing /boot/grub/menu.lst first, though.

---

### Post by ajgreeny on 2009-05-30
Do you have a USB drive to copy all the data files to, using the live ubuntu CD?  If so I think it would be a lot simpler to forget what may or may not already be on the disk, and where it happens to be as well, and start again with a clean disk installing XP to the whole disk as would normally happen.  You can then add back all your data files from the USB drive and should have a nice new good clean start.

If windows is really on an extended partition as it appears, then, like merlinus, I also think it will be pretty well impossible to get it to boot.

---

### Post by Salmontarre on 2009-05-30
Ok, so where I stand now, then is:

During the partitioning, the drive letters changed.  My backup partition is now C:/, and the XP installation is on D:/.

On the C:/ I have the boot.ini file:

```
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

And on D:/ I have the Windows folder and the System Volume Information folder.

Argh.  I don't got enough room to backup all my stuff on laptop.

---

### Post by merlinus on 2009-05-30
You might try the live gparted disk and move and/or resize existing partitions, leaving enough room at the beginning of the hdd to reinstall xp.  Then your data will be safe.

---

### Post by ajgreeny on 2009-05-30
OK.  Here's a possible but rather "dirty" way to get out of this situation.  Using the ubuntu live CD, copy all the files to the C storage drive, as you call it.  It should be obvious which it is as you will be able to see all the files in nautilus.  Now run the System-Administration-Partition Editor, and delete the other, now useless OS partitions.  That should leave you with free space in either one or more separate areas of the disk, and allow you to install windows to the first free space and use any other free space as another storage partition.

I have never installed windows to anything other than a complete disk and that was so long ago that I can't remember what happens and how you choose partitions to install to, but no doubt it will all become clear when you get to that point.

EDIT:  Oh!  Too slow!

---

### Post by kruegger on 2009-05-30
Your partition table needs cleaning. You could use testdisk to set the partition you want to keep on booting and delete everything else. 

[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") is free software you can obtain from any Ubuntu repository. Bear in mind that your Xp sistem is still in your hard disk but because of the partition table being messed up, your pc can't find the booting path.

This program helped me a lot when a I was in your shoes. Very helpful.

Good luck

---

### Post by Salmontarre on 2009-05-30
[Here's what gparted looks like.]("http://imgur.com/t7LbJ.jpg")

A friend says I should just delete the sda5 and sda1 container, then try to install windows again.  I will try that now, and if it doesn't work I'll try this "dirty" method.

Thanks for all the help, I appreciate it.

---

### Post by binary00mind on 2009-05-30
[CENTER][/CENTER]I have spent 1 hour reading all the posts concerning the problem You have on Your hands. 
Each of the posters had a valid point and/or advice regarding the matter.From my personal experience I would  
go for a fresh start.The testdisk is my best friend under Windows and Linux.
but You are beyond the point of using testdisk to write new MBR code or 
clean the Partition Tables, because there will be leftovers (corrupted)
in the backup of MBR called copy, CHS, EMBR, I have 11 portable HD With 
6 Linux OS. I have presently installed 2x Ubuntus 9.04 1 Xubuntu 9.04
PCLinuxOS 2009.1 and Wolvix. (I just traded Slackware for Xubuntu)
Also I have XP Pro & Vista Ultimatum.(My Loptop has 2x250 GB HD)
I did hundreds of installation of Windows and the Linux. and I learned 
the hard way that, MBR must be clean. 
Find the way to make a backup of Your files. Use ¨Kill Disk¨ program 
to erase the disk and You could use ¨MBR Works¨ program(under DOS) to re-set both MBR & EMBR.
The rule is that the first partition at the start of the disk should be a Primary one, Not Primary-Extended..
By All means, You do not have to do what I am proposing. But You 
or Your Sister, sooner or later will encounter some problems..
It is my personal opinion.
There are many DOS programs that can zero-out MBR & EMBR, running 
from the CD . 
All the programs that I have mentioned here, can be obtain as a freeware.

---

### Post by Salmontarre on 2009-05-30
OK, I got it fixed.

What I did was use gparted to delete sda5, then delete sda1.  Then I used all the unallocated space to make a new NTFS primary partition, which popped up as sda1!  I then deleted the boot.ini from sda2 just to make sure.

Yay.

So now windows is installed there and working fine.

Thanks for the help.

---

