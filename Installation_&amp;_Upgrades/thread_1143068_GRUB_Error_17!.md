---
title: "GRUB Error 17!"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by ooolongT on 2009-04-29
Ok, so I have been struggling with this for several days, and I can not seem to get GRUB working, so right now I am working off a Live CD (thank heavens for Live CDs!).

A little background; I dual boot Intrepid with Windows XP. One disk, two partitions (and swap) with Ubuntu as the priority.  I have had Ubuntu installed and use it regularly.  However, in this instance, I had been working in XP and when I tried to shut it down, my system froze. When I manually restarted it, I started getting error 17.



Here is what I get when I try to start the machine:
```

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

```
And then it freezes and I can do nothing.

Pressing nothing helps, including ESC although by hitting Delete, I can get into the BIOS.

So, first I ran fdisk -l:
```

Disk /dev/sda: 8015 MB, 8015314944 bytes
5 heads, 32 sectors/track, 97843 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x42ef8b00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              51       97844     7823424    c  W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36ace502

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

```
To my untrained eye, it looks like it is not showing the Ubuntu partition?

Anyway, that did not give me any useful info so I downloaded BootInfoScript 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and ran it to get a little more info (I have also attached this file in case it is needed).
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/hdc
 => No known boot loader is installed in the MBR of /dev/hdd
 => Windows is installed in the MBR of /dev/sda
 => No boot loader? is installed in the MBR of /dev/sdb

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13f84d83

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 729 MB, 729608192 bytes
255 heads, 63 sectors/track, 22 cylinders, total 356254 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: hdd ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdd: 4294 MB, 4294965248 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097151 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36ace502

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8015 MB, 8015314944 bytes
5 heads, 32 sectors/track, 97843 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42ef8b00

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064    15,654,911    15,646,848   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="B458C5A458C565A8" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda1: UUID="523469C53469AD23" LABEL="Misfortune" TYPE="ntfs" 
/dev/sdb1: LABEL="êþ;&#8212;n^	¶Î" UUID="5558-2865" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/Misfortune type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hda1 on /media/Local Disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)
/dev/hdd on /media/SystemRescueCD_1.1.7 type udf (ro,nosuid,nodev,uid=999)


================================ hda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/hdd

00000000  45 52 08 00 00 01 ca 80  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

```
So from this it seems that there is a vfat Ubuntu partition there.  Mental note... 

I forged on... and I found this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I followed it:
```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub>
      find /boot/grub/stage

Error 15: File not found

```
Yes, there really was that extra line return in there, not sure why. but obviously, it didn't work anyway.  So then I tried an alternative also from [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) as well.
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/root
mount: special device /dev/sda6 does not exist

```
But then I remembered that the file system was vfat, so I changed that.
```

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda6 /mnt/root
mount: special device /dev/sda6 does not exist

```
Another dead end.  

I almost gave up, then I saw this [http://ubuntuforums.org/showthread.php?t=1141360&highlight=grub+error+17](http://ubuntuforums.org/showthread.php?t=1141360&highlight=grub+error+17)

> 

sudo bash

sudo mount -f /dev/sda1 /mnt

fsck -y /dev/sda1

You'll see fsck ansering "Yes" to alot of things. This is normal and was done because of the -y option. You will want to run that command a second time or even more than that until you get a "clean run". For it to be a clean install that means that you shouldn't see any "Yes" anywhere in that run, otherwise fsck had to fix something and you'll want to run it again. All fsck is doing is making sure the disk is intact.



I followed it and I got this:
```

root@ubuntu:~# bash
root@ubuntu:~# mount -f /dev/sda1 /mnt
root@ubuntu:~# fsck -y /dev/sda1
fsck 1.40.2 (12-Jul-2007)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
root@ubuntu:~#

```

Lame, right?  So what the heck do I do now?

---

### Post by ooolongT on 2009-04-29
Ok, sorry that was a bit verbose, but I wanted to make sure that I covered everything. Bump!

---

### Post by upchucky on 2009-04-29
since the ubuntu partition or lack of is unintelligble, personally i would do the partitions manually using gparted and partedit, the reason i use both is because i have had one or the other fail and i still could recover and set up partitions with one when the other failed.

after partitioning and verifying that ubuntu does boot up to a graphical display before an actual install.

Install again, if you manage to recover the original install it may give you nothing but grief.

download supergrub disk, it will fix any grub errors.

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by ooolongT on 2009-04-30
Upchucky, Thanks for your help.  I did as you suggested, and got a copy of the super grub loader disk, but my comp will not boot from that disk, nor anyhting else besides a linux live CD ( I have successfully booted knoppix and Ubuntu).

Here is what I get when I try to boot from the Suber Grub Disk, or the Sysem Rescue CD:

```

Boot from CD :
Boot from CD : 

NTLDR is missing 
Press Ctrl+Alt+Del to restart.  

```

I have also replaced the NTLDR and NTLDR.COM files in the windows partition, and that has not made a difference. 

Any more suggestions?  Anyone?

---

### Post by unutbu on 2009-04-30
Am I right in assuming that Linux and XP were on the 120 GB drive?
It may be the case that somehow your partition table on the 120 GB drive got messed up.
If that is the case, testdisk may be able to recover your old partition table.

To use testdisk:

Boot the LiveCD. Open a terminal and type
```

cd ~/Desktop
wget http://www.cgsecurity.org/testdisk-6.11.2.linux26.tar.bz2
tar xvf testdisk*.tar.bz2
sudo testdisk-6.11.2/linux/testdisk_static
```

Select "No Log". Select the hard drive ("Disk") with Linux and XP on it.
Select "Proceed", "Intel", "Analyse", "Quick Search".
Press Enter and select "Deeper Search". This may take a while. 

Use the up/down arrows to move among your partitions.
Press 'p' to try to list files inside the partitions.
Look for any partition entry that shows files, particularly your missing Linux (and XP?) partitions.

Post here the output from the Deeper Search.

---

### Post by ooolongT on 2009-05-01
Ugh... this does not look good... 


TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/hda - 120 GB / 111 GiB - CHS 14593 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 14591 254 63  234420417 [Local Disk]

======================================
Utubu, please don't work on this right now, I think I may have found a partial solution, I will give mre details shortly.

---

### Post by ooolongT on 2009-05-06
Ok, I now know why things looked so kooky.  I was under the impression that there was only one hard drive with two partitions, not two hard drives with one partition a piece (which is how it is set up).  To make a long story short, I started a new thread here: [http://ubuntuforums.org/showthread.php?p=7223665#post7223665](http://ubuntuforums.org/showthread.php?p=7223665#post7223665)

---

### Post by ooolongT on 2009-05-13
I made some mistakes so I am abandoing this thread and opening a new one here [http://ubuntuforums.org/showthread.php?t=1150478](http://ubuntuforums.org/showthread.php?t=1150478)

Thanks for the help everyone!

---

