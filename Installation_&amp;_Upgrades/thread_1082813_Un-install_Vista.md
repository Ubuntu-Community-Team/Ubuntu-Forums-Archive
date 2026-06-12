---
title: "Un-install Vista"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by GriGGerS on 2009-02-28
Hi

I have decided to ditch windows full time and would like to un-install vista from my laptop.
I originally installed ubuntu with wubi. I have migrated everything to ubuntu and would like to keep this install.
Could someone point me in the right direction..  I have gparted installed and can see /dev/sda1 and /dev/sda2 but nothing that shows the partition that vista is on except that these are both NTFS partitions..

Thanks

GriGGerS

---

### Post by caljohnsmith on 2009-02-28
Probably sda2 is your Vista partition, but it would be good to check first before deleting sda1 and/or sda2. How about opening a terminal (Applications > Accessories > Terminal) and do::
```
sudo fdisk -lu
sudo mkdir /media/sda1 /media/sda2
sudo mount /dev/sda1 /media/sda1 
sudo mount /dev/sda2 /media/sda2
ls -l /media/sda1 /media/sda2
```
And please post the output of all the above commands.

---

### Post by GriGGerS on 2009-02-28
> **caljohnsmith said:**
> Probably sda2 is your Vista partition, but it would be good to check first before deleting sda1 and/or sda2. How about opening a terminal (Applications > Accessories > Terminal) and do::
```
sudo fdisk -lu
sudo mkdir /media/sda1 /media/sda2
sudo mount /dev/sda1 /media/sda1 
sudo mount /dev/sda2 /media/sda2
ls -l /media/sda1 /media/sda2
```
And please post the output of all the above commands.

Hi 

Thanks for your response.. The code as requested

```
nigel@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86c9c154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   234438655   115682304    7  HPFS/NTFS
nigel@ubuntu:~$ sudo mkdir /media/sda1 /media/sda2
nigel@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
nigel@ubuntu:~$ sudo mount /dev/sda2 /media/sda2
nigel@ubuntu:~$ ls -l /media/sda1 /media/sda2
/media/sda1:
total 3096
-rwxrwxrwx 1 root root 3170304 2006-09-18 13:45 boot.sdi
drwxrwxrwx 1 root root       0 2006-12-20 17:21 $RECYCLE.BIN
drwxrwxrwx 1 root root       0 2006-12-15 10:25 sources
drwxrwxrwx 1 root root       0 2008-01-04 19:18 System Volume Information

/media/sda2:
total 4500382
-rwxrwxrwx 2 root root          0 2008-08-05 08:52 20080805-085257.WAV
drwxrwxrwx 1 root root          0 2008-01-23 19:17 Apps
-rwxrwxrwx 2 root root          0 2008-08-05 08:52 AudioTestRec0.wav
-rwxrwxrwx 1 root root         24 2006-09-18 22:43 autoexec.bat
drwxrwxrwx 1 root root          0 2006-12-15 12:48 b177292c053a688aa3ef
drwxrwxrwx 1 root root       4096 2008-05-01 12:04 Boot
-rwxrwxrwx 1 root root     333203 2008-01-19 07:45 bootmgr
-rwxrwxrwx 1 root root       8192 2008-02-22 03:44 BOOTSECT.BAK
drwxrwxrwx 1 root root          0 2009-02-28 13:38 Config.Msi
-rwxrwxrwx 1 root root         10 2009-02-19 10:30 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:00 Documents and Settings
drwxrwxrwx 1 root root          0 2008-10-20 21:14 DVDneXtCopy
-rwxrwxrwx 1 root root    1700352 2001-09-05 21:00 gdiplus.dll
-rwxrwxrwx 1 root root 2145443840 2009-02-28 14:49 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-02-22 03:23 $INPLACE.~TR
drwxrwxrwx 1 root root          0 2008-12-18 12:45 Kontiki
drwxrwxrwx 1 root root       4096 2009-02-16 17:12 My Recordings
-rwxrwxrwx 1 root root 2459238400 2009-02-28 14:49 pagefile.sys
drwxrwxrwx 1 root root          0 2008-05-01 11:51 PerfLogs
drwxrwxrwx 1 root root          0 2008-10-02 18:39 PrepLogic
drwxrwxrwx 1 root root       8192 2009-02-25 21:09 ProgramData
drwxrwxrwx 1 root root          0 2008-10-10 09:12 ProgramDataNetwork LookOutNet Monitor for Employees Professional
drwxrwxrwx 1 root root      40960 2009-02-25 21:04 Program Files
drwxrwxrwx 1 root root       4096 2006-11-02 13:02 $Recycle.Bin
-rwxrwxrwx 1 root root       3315 2008-01-11 18:47 Startup.log
-rwxrwxrwx 1 root root        176 2006-12-21 06:25 SWSTAMP.TXT
drwxrwxrwx 1 root root      28672 2009-02-28 14:54 System Volume Information
drwxrwxrwx 1 root root       8192 2009-01-05 17:40 Temp
-rwxrwxrwx 2 root root     776460 2008-08-05 08:35 test_6008.mp3
drwxrwxrwx 1 root root      49152 2009-01-05 18:02 tmp
drwxrwxrwx 1 root root       4096 2008-01-04 19:34 Toshiba
drwxrwxrwx 1 root root       4096 2009-02-19 10:40 ubuntu
drwxrwxrwx 1 root root          0 2009-02-19 10:30 ubuntu-backup
drwxrwxrwx 1 root root       4096 2009-02-17 18:39 Users
-rwxrwxrwx 2 root root     475286 2006-12-15 11:50 vcredist_x86.log
drwxrwxrwx 1 root root       4096 2009-01-12 20:08 Web Sites
drwxrwxrwx 1 root root      32768 2009-02-14 18:06 Windows
drwxrwxrwx 1 root root          0 2008-02-22 03:26 $WINDOWS.~Q
drwxrwxrwx 1 root root          0 2008-04-19 08:13 WTablet
-rwxrwxrwx 1 root root     192307 2008-10-27 17:37 wubildr
-rwxrwxrwx 1 root root       8192 2008-10-27 17:37 wubildr.mbr
nigel@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2009-02-28
So it looks like sda1 is a really small recovery partition of some sort while sda2 is your main Vista partition. Did you want to keep Ubuntu on the same drive as Vista I assume? If so, you'll need to migrate Ubuntu to its own partition, which you can do with "LVPM":

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

How large is your Ubuntu partition (root.disk) in Vista? In order to create a new partition for Ubuntu, you will have to resize your Vista partition first, and you can do that with gparted from the Live CD (System > Admin > Partition Editor). Or you might be able to use Vista's own disk management tools to shrink Vista by enough to make room for a Ubuntu partition. Personally what I would recommend though is booting into your Ubuntu install, save all your personal files to another HDD, and then use the Live CD to do a fresh install of Ubuntu to the Vista drive so that it uses the entire drive. Good luck and let me know how it goes.

---

### Post by GriGGerS on 2009-02-28
Hi 

Ok I think the fresh install may be the way to go...  Just one question.. I have converted all of my emails ect ect and now have them in evolution.. 
Most of this I have done in the home directory..  I assume if i copy the home directory all of my personal files will be saved? Can i then just replace the folders in the new install ie for evolution with the new ones to recover my emails?

Sorry if this is an obvious question but I am a linux noob..

Cheers 

GriGGerS

---

### Post by caljohnsmith on 2009-02-28
> **GriGGerS said:**
> Just one question.. I have converted all of my emails ect ect and now have them in evolution.. 
Most of this I have done in the home directory..  I assume if i copy the home directory all of my personal files will be saved? Can i then just replace the folders in the new install ie for evolution with the new ones to recover my emails?

Yes, all your personal documents should be in your home directory unless you deliberately saved some of them somewhere else. And you can probably replace your evolution directory in the new install with your current evolution directory and it will work fine. Good luck and let me know how it goes.

---

### Post by GriGGerS on 2009-03-09
Hi caljohnsmith.. All went fine.. Now 100% ubuntu..  

Cheers

---

