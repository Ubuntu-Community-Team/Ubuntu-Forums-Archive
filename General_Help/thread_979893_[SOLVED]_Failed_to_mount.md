---
title: "[SOLVED] Failed to mount"
date: 2008-11-12
forum: General Help
---

### Post by karlmp on 2008-11-12
Ubuntu hardy heron 8.04.1

when i insert and try to mount my flash drive i get this message:

Failed to mount "256M Removable Volume".

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.

```
karl@karlzt:~$ dmesg | tail 
[  302.339860] sd 2:0:0:0: [sdb] Write Protect is off
[  302.339870] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  302.339876] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  302.339885]  sdb: sdb1
[  302.342492] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  302.342589] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  317.695492] UDF-fs: No partition found (1)
[   90.718260] ISOFS: Unable to identify CD-ROM format.
[  624.743395] UDF-fs: No partition found (1)
[  624.813925] ISOFS: Unable to identify CD-ROM format.
```

thanks in advance

---

### Post by vanadium on 2008-11-12
This indicates that Ubuntu does not recognize a valid partition on your USB. It might be broken or might have been corrupted. In the latter case, you will be able to repair it by repartitioning and formatting.

---

### Post by karlmp on 2008-11-12
i just mounted and unmounted following the instructions here: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

how can i make it mount using the GUI?

---

### Post by john183 on 2008-11-12
I am going to venture a guess that your thumbdrive is a "U3 Smart" drive. Linux will most likely have an issue with the "CDROM" portion of the drive as it is only compatible with Windows. If you google "removing U3 software" you can find the windows executable file to remove the U3 portion of the thumbdrive and make it just a plain old thumbdrive that will work with any os.

---

### Post by vanadium on 2008-11-12
@john183: The "UDF-fs:" in the output of dmesg surely may point in that direction. Would it be possible to remove that U3 software the Ubuntu way, i.e. by repartitioning the drive?

---

### Post by karlmp on 2008-11-12
it isn't u3 'the devil' how i call it, actually i had it in one of my flash drives and i removed it from windows

the flash drive that I'm mounting is old so it didn't come with that

i used these drives in Ubuntu previously with no problem 



i did a fresh install of ubuntu using a flash drive 2 days ago

---

### Post by john183 on 2008-11-12
> **karlmp said:**
> it isn't u3 'the devil' how i call it, actually i had it in one of my flash drives and i removed it from windows

the flash drive that I'm mounting is old so it didn't come with that

i used these drives in Ubuntu previously with no problem 



i did a fresh install of ubuntu using a flash drive 2 days ago

Based on this information i think your only way to make the drive usable again may be to reformat the drive. it looks as if the fs or maybe the file allocation table (if it was a FAT16/32 drive) is corrupted.

---

### Post by john183 on 2008-11-12
> **vanadium said:**
> @john183: The "UDF-fs:" in the output of dmesg surely may point in that direction. Would it be possible to remove that U3 software the Ubuntu way, i.e. by repartitioning the drive?

Unfortunately, as far as I know there is no way other than the windows program to remove the U3 software. But then again, i have never tried to just completely repartition and reformat a U3 drive in linux, it may work.

---

### Post by karlmp on 2008-11-12
i just tested it in windows and works OK in there

i removed bluetooth few minutes later that i installed Ubuntu 2 days ago, maybe it has to do with that?

---

### Post by karlmp on 2008-11-12
i reformatted the drive but the problem persists

---

### Post by vanadium on 2008-11-13
There must be something not standard with the drive. With the drive plugged in, issue the commands

```

sudo fdisk -l
mount

```

and post the output here. this will learn how linux sees the drive. You might need to repartition the usb disk before reformatting, or at least just 'correct' the partition table.

---

### Post by karlmp on 2008-11-13
```
karl@karlzt:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74e774e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda3            3649        4870     9815715    5  Extended
/dev/sda5            4802        4870      554211   82  Linux swap / Solaris
/dev/sda6            4733        4801      554179+  82  Linux swap / Solaris
/dev/sda7            4680        4732      425659+  82  Linux swap / Solaris
/dev/sda8            3649        4679     8281444+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4110 MB, 4110227968 bytes
16 heads, 63 sectors/track, 7964 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x000eaf9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7965     4013863    b  W95 FAT32

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x69489b85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979      250574+   b  W95 FAT32

Disk /dev/sdd: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x4c903b76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         993      500355+   b  W95 FAT32
karl@karlzt:~$ mount
/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/karl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=karl)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)
/dev/sdd1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)


```

as you can see, there are three flash drives plugged in

---

### Post by karlmp on 2008-11-13
ok :confused: now something new:

when i plug in the first drive it won't mount, but when i plug in the second drive it mounts :confused:

when i plug in the first drive Linux see the drive as /media/cdrom0, when i plug in the second Linux see it as /media/disk then when i plug in the third Linux see it as /media/disk-1

the first it won't mount, but the other two mounts

to mount the first i have to go to Gparted and tell it to mount on /media/cdrom0

how i fix this?

---

### Post by vanadium on 2008-11-14
Theser are vfat (FAT) formatted USB sticks. Before proceeding, you should check if the file system of these drives is consistent. To do that: 1) first unmount the drive 2) perform a file system check

```

sudo umount /dev/sdb1
sudo fsck /dev/sdb1

```

If the second command indicates errors, you need to actually repair the file system: add the -a option or the -r option (see "man dosfsck" for details). this is equivalent to running "chkdsk a: /f" under windows.

Then I suggest you give your USB drives meaningful names (a volume label). Then Ubuntu will automatically use the name of the label as the mount point. Now it is using a generic name and maybe the problem you have is due to mount points not being removed when something goes astray, and causing problems when a system attempts to mount another drive on the same mount point.

On this page: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
you can see how volume labels can be given. Unfortunately, the procedure is different for different file systems. Your drives are vfat formatted. You will therefore need to apply the procedure "Changing the Label" for "FAT16 and FAT32" using mtools.

Finally, I suggest you clean up "left over" mount points under /media. If no external devices are actually mounted, /media normally contains only mount points for cdrom. All the other mount points can be deleted. First make sure all external drives are unmounted. Then use a nautilus instance with root permissions ("gksu nautilus") to navigate to /media and delete any mount point that is not for cdrom.

---

### Post by karlmp on 2008-11-14
i found this: [http://forum.eeeuser.com/viewtopic.php?pid=354743](http://forum.eeeuser.com/viewtopic.php?pid=354743)

i removed the last two lines in /etc/fstab:

```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

and now when i plug in the drive, it mounts:)

---

### Post by vanadium on 2008-11-15
The line for sdb1 indeed is very strange. scd0 however denotes a CD rom. If you have issues with your CD rom, try to put that last line back. If however all is working well, you are fine. Congratulations that you found the solution yourself!

---

### Post by karlmp on 2008-11-15
[SIZE="7"]thanks[/SIZE]

---

