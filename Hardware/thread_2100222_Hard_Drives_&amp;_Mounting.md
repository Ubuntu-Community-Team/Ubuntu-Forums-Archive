---
title: "Hard Drives &amp; Mounting"
date: 2013-01-01
forum: Hardware
---

### Post by bman on 2013-01-01
Hey,

I am having all kinds of issues with mounting my drives. 

I am trying to give Plex Media Server permissions to access the files on those drives. I have been successful with one of them but not the others.

This is hard and a lot to explain.

I have 3 1TB drives, 1 2TB drive in total. 1 of the 1TB drives has the OS on it, 2 of them are media, and the 2TB is media.

I originally had Windows 8 installed, and moved to Ubuntu 12.04. Since then having all kinds of problems with the drives.

First off, even though Windows 8 is completely wiped, I still have the grub offering Windows 8. Secondly, using Storage Device Manager I can't seem to change any settings/permissions to the drives, except for the 2TB drive.

Because of whatever I have done or haven't done, sometimes I can mount the two 1TB drives, sometimes I can't. On boot it gives an error that it couldn't mount sda1 (one of the 1TB drives).

Storage drives should be formatted as what for Linux? They are all NTFS at the moment and I assume that is fine. But I am having the feeling my problems are because they are NTFS drives that came from a Windows machine.

I don't know if I explained enough, or well enough but I am hoping someone can help me. I feel like I have to wipe/format all the drives clean and start over, but the amount of data I have (and no where to move it to) it's a problem to do that.

---

### Post by sudodus on 2013-01-01
> **bman said:**
> ...
First off, even though Windows 8 is completely wiped, I still have the grub offering Windows 8.

If everything from Windows 8 is wiped, and you run
```
sudo update-grub
``` it won't appear as a boot option. But maybe a recovery partition is still there.
> 

Secondly, using Storage Device Manager I can't seem to change any settings/permissions to the drives, except for the 2TB drive.
Windows file systems, FAT and NTFS, get their permission settings in linux when mounted, and you cannot change them afterwards. This is normal, and the permissions can be changed with an entry in the file [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT].
> 

Because of whatever I have done or haven't done, sometimes I can mount the two 1TB drives, sometimes I can't. On boot it gives an error that it couldn't mount sda1 (one of the 1TB drives).
This is strange.
> 
Storage drives should be formatted as what for Linux? They are all NTFS at the moment and I assume that is fine. But I am having the feeling my problems are because they are NTFS drives that came from a Windows machine.

I don't know if I explained enough, or well enough but I am hoping someone can help me. I feel like I have to wipe/format all the drives clean and start over, but the amount of data I have (and no where to move it to) it's a problem to do that.

If you save your data and repartition/reformat your drives to linux ext formats, things will work better in linux. The drivers for the native file systems are much more efficient. Particularly the drivers for NTFS are slow. And the management of permissions works for individual files and directories.

Ext2 is the oldest file system, and has no journaling. Ext3 is newer and very stable. Ext4 is the newest and fastest one. Both ext3 and ext4 have journaling. Ext4 is recommended at least for the root file system. Ext2 is recommended for USB flash drives, since the lack of journaling keeps down the amount of write operations. (SSD drives have higher quality and can be used with ext4.)

Windows won't read the ext file systems unless you add a special driver, see

[[COLOR="Red"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by bman on 2013-01-01
I did the sudo update-grub and came back and found the Windows 8 loader, says its on sda1, which was not the drive that originally had Windows 8 on it, so that is quite weird.

I think my best bet is to find a way to move all the data off, and wipe and format in ext4. Though I don't know how I am going to do that.

Once these are in ext4, can I change permissions easier? Like can I just right click on them, properties, etc...and change it? Or still command line stuff?

---

### Post by sudodus on 2013-01-01
> **bman said:**
> ...
I think my best bet is to find a way to move all the data off, and wipe and format in ext4. Though I don't know how I am going to do that.

Use gparted booted from another drive (not the one to edit). So either boot from the Ubuntu install drive or install gparted into your Ubuntu system (if it is installed on a drive, that you won't edit).
```
sudo apt-get install gparted
``` and run it with superuser privileges
```
gksudo gparted
``` or from the menu.
Select the appropriate drive to edit at the top right corner.

Select
***Device -- Create Partition Table***
or something similar, it is translated to the language installed. The standard is MSDOS or MBR. After that select
***Partition -- New***
and create the partition(s).
> 

Once these are in ext4, can I change permissions easier? Like can I just right click on them, properties, etc...and change it? Or still command line stuff?

Yes. For me it is easiest with command line stuff, but it works with the GUI stuff too, using the file browser ;-) If the computer works properly, these external drives should work like internal (except maybe that they are slower due to the USB 2 speed limit).

But you described issues that indicate that the computer might not recognize the drives properly. We don't know the cause of that yet.

---

### Post by Wim Sturkenboom on 2013-01-01
> **bman said:**
> I did the sudo update-grub and came back and found the Windows 8 loader, says its on sda1, which was not the drive that originally had Windows 8 on it, so that is quite weird.
I don't think it's weird. A Windows install nowadays has often two partitions, one for the bootloader and one for the OS itself; my Win7 system has that as well. I think it's UEFI related.

That's all I can help you with at this moment.

---

### Post by bman on 2013-01-01
Thanks guys.

Firstly, I never said these drives were external, they are internal drives. I also was not asking how to format/partition, when I said I don't know how I am going to do that, I was referring to where to backup my data too lol

But thanks for the info.

Will update when I complete the formating.

*I do have one question.

When partitioning,

Free Space preceding (MiB), it's always 1, can't make it lower. Is that needed for some reason?

Is it suppose to be a Primary Partition or Extended (storage only/media)?

And Align too is always set to MiB, is that correct?

---

### Post by sudodus on 2013-01-01
> **bman said:**
> Thanks guys.

Firstly, I never said these drives were external, they are internal drives. I also was not asking how to format/partition, when I said I don't know how I am going to do that, I was referring to where to backup my data too lol

OK, sorry for drawing too quick conclusions.
> 
...
*I do have one question.

When partitioning,

Free Space preceding (MiB), it's always 1, can't make it lower. Is that needed for some reason?

Gparted makes it like that: 2048 sectors of 512 bytes (1 MiB). I think it is space for modern boot sectors, partitions and such things. I used fdisk and made it smaller some months ago, and had problems, so it is not completely wasted.
> 
Is it suppose to be a Primary Partition or Extended (storage only/media)?

I'm not sure I get what you mean. The first partition can be an extended partition, that is OK with linux, but at least earlier, Windows needed a primary partition.
> 
And Align too is always set to MiB, is that correct?
It is probably more efficient for reading and writing, but I don't know if it's necessary.

---

### Post by bman on 2013-01-01
Thanks,

The Primary Question, I was saying these drives are going to be used for media/storage, no OS, should it be Primary or Extended. I guess it does not matter, will go Primary.

*I am on the Live CD, using Gparted.

I deleted the partition (sdc1), created a new one as ext4, then even formatted again after that. It's still showing 14.81GiB used. HOW is that possible?

When I go back into my Ubuntu installation, I get this when trying to mount it.

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 12 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad; rest of file ignored
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab

---

### Post by sudodus on 2013-01-01
> **bman said:**
> Thanks,

The Primary Question, I was saying these drives are going to be used for media/storage, no OS, should it be Primary or Extended. I guess it does not matter, will go Primary.

That's right, it does not matter.
> 
*I am on the Live CD, using Gparted.

I deleted the partition (sdc1), created a new one as ext4, then even formatted again after that. It's still showing 14.81GiB used. HOW is that possible?

I guess you expect the partition to be larger. Maybe you try to make a partition that is larger than can be managed by the bios, operating system or something else in the computer.
> 
When I go back into my Ubuntu installation, I get this when trying to mount it.

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 12 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad; rest of file ignored
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab
After repartitioning, the drive will get a new UUID and if that is used (which is recommended), you must change the entry in fstab accordingly.

Please mount all drives that can be mounted and post the output of the following commands
```
df
```
```
sudo fdisk -lu
```
```
sudo blkid
```

---

### Post by bman on 2013-01-01
Path:/home/bman                                                                                        
  .dmrc                           26 13-01-01 11:44   .bash_logout                   220 12-12-31 21:27
  .profile                       675 12-12-31 21:27   .pulse/                      <DIR> 13-01-01 11:44
  .mission-control/            <DIR> 12-12-31 21:54   .ICEauthority                 1980 13-01-01 11:44
  Pictures/                    <DIR> 12-12-31 21:54   .gnome2/                     <DIR> 12-12-31 21:54
  .gstreamer-0.10/             <DIR> 13-01-01  0:39   .mozilla/                    <DIR> 12-12-31 23:41
  examples.desktop              8445 12-12-31 21:27   .cache/                      <DIR> 12-12-31 23:46
  .compiz-1/                   <DIR> 12-12-31 23:05   Videos/                      <DIR> 12-12-31 21:54
  Downloads/                   <DIR> 13-01-01  2:07
  Public/                      <DIR> 12-12-31 21:54
  Music/                       <DIR> 12-12-31 21:54
  .xsession-errors.old         16799 13-01-01 11:21
  Desktop/                     <DIR> 12-12-31 21:54
  .pki/                        <DIR> 12-12-31 23:43
  .config/                     <DIR> 13-01-01  0:10
  Documents/                   <DIR> 12-12-31 21:54
  .bash_history                   86 13-01-01 12:28
  .xsession-errors              3261 13-01-01 12:27
  .pulse-cookie                  256 12-12-31 21:54
  .bashrc                       3486 12-12-31 21:27
  .gvfs/                       <DIR> 13-01-01 11:44
  .goutputstream-THAFQW            0 12-12-31 23:02
  ./                           <DIR> 13-01-01 11:44
  .goutputstream-KWXFQW            0 12-12-31 23:19
  .gconf/                      <DIR> 13-01-01 11:44
  ../                          <DIR> 12-12-31 21:27
  .dbus/                       <DIR> 12-12-31 21:54
  .Xauthority                     54 13-01-01 11:44
  .thumbnails/                 <DIR> 12-12-31 23:40
  Templates/                   <DIR> 12-12-31 21:54
  .local/                      <DIR> 12-12-31 21:54
  .gksu.lock                       0 13-01-01 11:46
  .gtk-bookmarks                 132 13-01-01 11:44


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0875b3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00058157

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1936750591   968374272   83  Linux
/dev/sdb2      1936752638  1953523711     8385537    5  Extended
/dev/sdb5      1936752640  1953523711     8385536   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000087d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   83  Linux

Disk /dev/sdd: 16.0 GB, 16049504256 bytes
255 heads, 63 sectors/track, 1951 cylinders, total 31346688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042417

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    31346687    15673312+   c  W95 FAT32 (LBA)

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  3907029167  1953514583+  ee  GPT


/dev/sda1: LABEL="TV Shows" UUID="264440F74440CB6F" TYPE="ntfs" 
/dev/sdb1: UUID="eb97f4c9-e9aa-493f-b9b7-4a90e3f0eb38" TYPE="ext4" 
/dev/sdb5: UUID="7875a1c3-adb6-4e13-b108-25ba799f32af" TYPE="swap" 
/dev/sdc1: LABEL="Media" UUID="dbebf77d-356a-4a03-8998-be5d8d05c935" TYPE="ext4" 
/dev/sdd1: LABEL="Terminator" UUID="9E75-1449" TYPE="vfat" 
/dev/sde2: LABEL="Movies" UUID="7A0CCD330CCCEAE9" TYPE="ntfs" 


I hope that is the correct information.

---

### Post by sudodus on 2013-01-01
Quick reply: I think the first output was from some ls command. I asked for 'disk free'

```
df
```
If you have an alias df that captures the command, try
```
\df
```

---

### Post by sudodus on 2013-01-01
> **bman said:**
> Thanks,

I deleted the partition (sdc1), created a new one as ext4, then even formatted again after that. It's still showing 14.81GiB used. HOW is that possible?

```
 Device Boot Start End Blocks Id System
 /dev/sdc1 2048 1953523711 976[COLOR="Red"]760[/COLOR]832 83 Linux
```
This is almost 1 TB, how did you see it as 14.81GiB? Did you mix it up with 
```
/dev/sdd1 * 63 31346687 15673312+ c W95 FAT32 (LBA)
```

---

### Post by sudodus on 2013-01-01
Finally I would ask for the output of
```
cat /etc/fstab
```

---

### Post by bman on 2013-01-01
df

Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sdb1       953178004    5032248 899727044   1% /
udev              4079876         12   4079864   1% /dev
tmpfs             1635472        928   1634544   1% /run
none                 5120          0      5120   0% /run/lock
none              4088676       5496   4083180   1% /run/shm
/dev/sdd1        15658000     732872  14925128   5% /media/Terminator
/dev/sda1       976759804  867476380 109283424  89% /media/TV Shows_
/dev/sde2      1953512444 1297116960 656395484  67% /media/Movies_
/dev/sdf1      1953511420 1896348792  57162628  98% /media/External Media

cat /ect/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc              proc  nodev,noexec,nosuid                                            0  0  
# / was on /dev/sdc1 during installation
UUID=eb97f4c9-e9aa-493f-b9b7-4a90e3f0eb38  /                  ext4  errors=remount-ro                                              0  1  
# swap was on /dev/sdc5 during installation
/dev/sdc1                                  /media/TV Shows 2  ntfs  nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner  0  0  
/dev/sdd2                                  /media/Movies      ntfs  nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner,uid=plex  0  0  
/dev/sdc1                                  /media/TV Shows 2  ntfs  nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner           0  0  
/dev/sdc1                                  /media/TV Shows 2  ntfs  nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner,uid=root  0  0  
/dev/sdb5                                  /media/TV Shows    swap  users,sw,user,owner                                            0  0  
/dev/sdc1                                  /media/TV Shows 2  ntfs  nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner,uid=root  0  0  
/dev/sdb5                                  /media/TV Shows    swap  users,user,owner                                               0  0  
/dev/sdc1                                  /media/TV Shows 2  ntfs  defaults                                                       0  0  
/dev/sdc1                                  /media/TV Shows 2  ntfs  nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner,uid=plex  0  0 

I see the 14GB used in Gparted. Says 931.51GiB size, and 14.81GiB Used, and 
916.70 Unused. for sdc1.

---

### Post by Wim Sturkenboom on 2013-01-01
Your fstab is a bit of a mess, by the looks of it. You have multiple entries for sdb5 and sdc1. The cause for the errors is (more than likely) the space in "TV Shows".

I would remove all entries that gave errors in post #8 (actually I would remove all entries refering to sdc1 and sdb5; sdd2 is OK). Next I would mount sdc1 using Nautilus (click on the drive in the device section in the left pane). Once your disk content shows in the right hand pane, use a terminal and run the command _cat /etc/mtab_
```

wim@i3-2120:~$ **[COLOR="Red"]cat /etc/mtab[/COLOR]**
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda6 /home ext4 rw 0 0
/dev/sdc1 /mnt/photos ext3 rw 0 0
gvfs-fuse-daemon /home/wim/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=wim 0 0
[COLOR="Red"]/dev/sdb1 /media/WinXP fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0[/COLOR]
wim@i3-2120:~$ 

```
In above example it is sdb1 that was mounted using Nautilus; copy that line into /etc/fstab.
Next unmount it in nautilus and mount it manually in a terminal using the below command; this to check if the entry in /etc/fstab is correct
```

sudo mount /dev/sdb1

```
If that works, unmout it using
```

sudo umount /dev/sdb1

```

Next I would finetune the entry
1)
replace /dev/sdb1 by it uuid; to determine the uuid, run _sudo blkid_
```

wim@i3-2120:~$ **[COLOR="Red"]sudo blkid[/COLOR]**
/dev/sda1: LABEL="System Reserved" UUID="E05A431C5A42EEBA" TYPE="ntfs" 
/dev/sda2: LABEL="Win7" UUID="54C65509C654ECAC" TYPE="ntfs" 
/dev/sda3: UUID="15274769-0777-4a8e-a167-ec7501f8665a" TYPE="swap" 
/dev/sda5: UUID="2e61cbc5-d982-4ada-8af7-cbdea09bb295" TYPE="ext4" 
/dev/sda6: UUID="0a1c5d63-223f-4dc3-9ab8-46f566f5fa7b" TYPE="ext4" 
[COLOR="Red"]/dev/sdb1: LABEL="WinXP" UUID="2020F32C20F30814" TYPE="ntfs" [/COLOR]
/dev/sdb5: LABEL="WinXPData" UUID="20982C20982BF2C8" TYPE="ntfs" 
/dev/sdb6: LABEL="SHARED_FAT" UUID="880A-66E0" TYPE="vfat" 
/dev/sdb7: UUID="c7f8f5d5-d24e-43ac-9b7f-2b31804a58ac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="0173d67a-bb5c-43bf-91c8-1fe03c5ff641" TYPE="swap" 
/dev/sdb9: UUID="ba587de2-a984-4d69-9070-17b17aeed06b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="photos" UUID="6ff7017c-e4d9-49ba-9a1b-b62e45dab820" TYPE="ext3" 
wim@i3-2120:~$ 

```
The line in fstab will now become (change in red)
```

[COLOR="Red"]UUID="2020F32C20F30814"[/COLOR] /media/WinXP fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

```
Test it again by mounting and unmounting manually

2)
/media is, in my opinion, for media like external disks that get connected and disconnected; if this is an internal disk that needs to be mounted at startup, use /mnt instead
```

sudo mkdir /mnt/TV_Shows

```
The line in fstab will now become (change in red)
```

UUID="2020F32C20F30814" [COLOR="Red"]/mnt/TV_Shows[/COLOR] fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

```
Test by mounting /mnt/TV_Shows

```

sudo mount /mnt/TV_Shows

```

Please note that you need to replace sdb1 in my examples by the partition (e.g. sdc1) that applies to your situation.

---

### Post by Wim Sturkenboom on 2013-01-01
And the last step would probably be to create some symbolic links to the mount points on e.g. the desktop or somewhere in your home directory/

---

### Post by bman on 2013-01-01
When I run the command cat /etc/mtab I get this.

/dev/sdc1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sde1 /media/Terminator vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0
/dev/sdb1 /media/External\040Media fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdd1 /media/Media ext4 rw,nosuid,nodev,uhelper=udisks 0 0
/dev/sdf2 /media/Movies_ fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda1 /media/TV\040Shows_ fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
gvfs-fuse-daemon /home/bman/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=bman 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0

So what am I suppose to be copying into fstab, which I do not know how to do as well.

Note the one that was TV Shows, I tried labeling Shows, and there is now another drive, external attached. Just in case it looks differnet.

---

### Post by sudodus on 2013-01-01
> **bman said:**
> 
I see the 14GB used in Gparted. Says 931.51GiB size, and 14.81GiB Used, and 916.70 Unused. for sdc1.

Yes. The administration of the ext4 file system needs a certain percentage of the total size. This is normal.
--
0. Next time, please put input to and output from terminal windows in code tags like this

[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

It is easily done by marking it and clicking on the **#** icon at the top of this editing window.
--
1. Now I'll try to summarize the information:

```
a. Disk /dev/sda: 1000.2 GB
partition
/dev/sda1 2048 1953521663 976759808 7 HPFS/NTFS/exFAT
LABEL="TV Shows" UUID="264440F74440CB6F" TYPE="ntfs"
Filesystem 1K-blocks Used     Available Use% Mounted on 
/dev/sda1  976759804 867476380 109283424 89% /media/TV Shows_
/etc/fstab: no entry

b. Disk /dev/sdb: 1000.2 GB
partitions
/dev/sdb1 * 2048 1936750591 968374272 83 Linux (* <--> boot)
UUID="eb97f4c9-e9aa-493f-b9b7-4a90e3f0eb38" TYPE="ext4"
Filesystem 1K-blocks Used    Available  Use% Mounted on 
/dev/sdb1  953178004 5032248   899727044  1% / (root file system)
/etc/fstab:
 UUID=eb97f4c9-e9aa-493f-b9b7-4a90e3f0eb38 / ext4 errors=remount-ro 0 1  (/ <--> root file system)

/dev/sdb2 1936752638 1953523711 8385537 5 Extended

/dev/sdb5 1936752640 1953523711 8385536 82 Linux swap / Solaris
UUID="7875a1c3-adb6-4e13-b108-25ba799f32af" TYPE="swap" 
Filesystem not mounted
/etc/fstab:
/dev/sdb5 /media/TV Shows swap users,user,owner 0 0 

c. Disk /dev/sdc: 1000.2 GB
partition
/dev/sdc1 2048 1953523711 976760832 83 Linux
LABEL="Media" UUID="dbebf77d-356a-4a03-8998-be5d8d05c935" TYPE="ext4" 
Filesystem not mounted
/etc/fstab: 6 entries, all bad

d. Disk /dev/sdd: 16.0 GB
partition
/dev/sdd1 * 63 31346687 15673312+ c W95 FAT32 (LBA) (* <--> boot)
LABEL="Terminator" UUID="9E75-1449" TYPE="vfat" 
Filesystem 1K-blocks  Used Available Use% Mounted on
/dev/sdd1   15658000 732872 14925128   5% /media/Terminator
/etc/fstab: no entry
 
/dev/sdd2 (no such partition now)
/etc/fstab:
/dev/sdd2 /media/Movies ntfs nls=iso8859-1,ro,users,umask=000,gid=bman,user,owner,uid=plex 0 0 (left from previous configuration)

e.  Disk /dev/sde: 2000.4 GB
partition
/dev/sde1 1 3907029167 1953514583+ ee GPT (fdisk cannot manage it)
/dev/sde2: LABEL="Movies" UUID="7A0CCD330CCCEAE9" TYPE="ntfs"  - (blkid sees 'the same' as df)
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sde2 1953512444 1297116960 656395484 67% /media/Movies_
/etc/fstab: no entry

f. No disk
Filesystem 1K-blocks      Used Available Use% Mounted on
/dev/sdf1 1953511420 1896348792  57162628 98% /media/External Media
(mounted -- maybe not at the same time as fdisk and blkid)
/etc/fstab: no entry
```

2. Comments

Use labels to identify partitions but ***avoid spaces in the labels***.

The /etc/fstab file has several bad lines and needs editing. First, delete the entries for /dev/sdc1 and the entry for /dev/sdd2. Later on we can create good entries for the relevant partitions, /dev/sdc1 and some other partitions. It is safest to use UUID to identify a partition, but it is pretty safe and quite transparent to use labels too.

---

### Post by bman on 2013-01-01
So I got annoyed and impatient and did some calculations. 

I removed all drives from my system, wiped and formatted my main drive used for the OS, ext4 partition. Installed ubuntu and left it at that. 

I am now plunging in my other drives into a windows system and complicatedly backing up and wiping/formatting them in ext4 partitions. 

It's going to take long but should work and fix all my problems. 

If not, I will be back posting in this thread. 

Thanks.

---

### Post by bman on 2013-01-02
Alright,

So I have all my drives partitioned as ext4 now. When I Right Click, Properties, Permissions on the drives or anything within the drive I get Owner & Group as root, and at the bottom it says "You are not the owner, so you cannot change these permissions"

Is this normal? I can't even delete or move the files on the drives.

So how to I change these, I thought once they were ext4 I could just go into that menu and change it, but is all blanked out.

---

### Post by Wim Sturkenboom on 2013-01-03
Where do you right click on the drives? I simply don't know what you mean by that and it confuses me a bit.
How do you mount them? Using /etc/fstab? If so, post the result of _cat /etc/fstab_. Or do you just double click them under devices in Nautilus?
How did you copy the files? Using sudo?

More questions than answers ;)

This is my setup for an ext3 partition (/dev/sdc1) that is mounted on startup under /mnt/photos
```

wim@i3-2120:~$ **[COLOR="Red"]ls -ld /mnt[/COLOR]**
drwxr-xr-x 4 root root 4096 Sep 16 18:28 /mnt
wim@i3-2120:~$ **[COLOR="Red"]ls -l /mnt[/COLOR]**
total 8
drwxr-xr-x 9 root root 4096 Sep 12 18:00 boot-sav
[COLOR="Red"]drwxr-xr-x 6 root root 4096 Dec 22  2010 photos[/COLOR]
wim@i3-2120:~$ 

```
My /etc/fstab is shown below
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=2e61cbc5-d982-4ada-8af7-cbdea09bb295 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0a1c5d63-223f-4dc3-9ab8-46f566f5fa7b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=15274769-0777-4a8e-a167-ec7501f8665a none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=0173d67a-bb5c-43bf-91c8-1fe03c5ff641 none            swap    sw              0       0

# photos (/dev/sdc1)
[COLOR="Red"]UUID="6ff7017c-e4d9-49ba-9a1b-b62e45dab820" /mnt/photos ext3 defaults 0 2[/COLOR]

```
And I have a shortcut on my desktop for easy access
```

wim@i3-2120:~$ **[COLOR="Red"]ls -l Desktop/[/COLOR]**
total 0
lrwxrwxrwx 1 wim wim 12 Sep 16 19:35 photos -> /mnt/photos/
wim@i3-2120:~$ 

```

Note 1:
You need to adjust this information to your needs; uuid will be different, filesystem is different etc

Note 2:
posted at 8:00 am so you have an idea of the time difference in case you still want me to help you remotely

---

### Post by sudodus on 2013-01-03
You created the file system as root, and root is the owner.

But you can change that, either for the whole drive or for some particular directories. Let's say, that you want to create the directory Photos and give your user ownership of it (which means permissions to do more than other users).

Try this method: Change directory so that the current directory is the 'root' directory of the newly formatted drive. I don't know where it is mounted, but let's say it is mounted on ***/media/multimed***
```
cd /media/multimed
```
```
sudo mkdir Photos
```
```
sudo chown bman:root Photos
``` or if you prefer
```
sudo chown bman:bman Photos
``` so that both user and group ownership belong to your user id (change to your actual user id if different from your Ubuntu nickname 'bman').

---

### Post by bman on 2013-01-03
Let's use one of the drives to work with.

I have a 1TB drive mounted and labeled as Shows.

I want that drive and everything under it owned by me, or at least editable by me.

When in nautilis, right click on it, properties. It says it is at /media

So would the directory of the drive be /media/Shows ?

So then I would do

```
cd /media/Shows
```

Then since that is the directory I want, I do...

```
sudo chown bman:root Shows
```

Is that correct?

Well the next step would be adding Plex to my group, so would doing bman:bman be better?

---

### Post by sudodus on 2013-01-03
> **bman said:**
> Let's use one of the drives to work with.

I have a 1TB drive mounted and labeled as Shows.

I want that drive and everything under it owned by me, or at least editable by me.

When in nautilis, right click on it, properties. It says it is at /media

So would the directory of the drive be /media/Shows ?

So then I would do

```
cd /media/Shows
```

Then since that is the directory I want, I do...

```
sudo chown bman:root Shows
```

Is that correct?

Well the next step would be adding Plex to my group, so would doing bman:bman be better?

Yes, try using those commands!

If you are not really interested in doing things with the files and directories as root, and you want Plex to do it,

bman:bman

should be OK, maybe better. Check the spelling: is the user id Plex or plex?

---

### Post by Wim Sturkenboom on 2013-01-03
chown will not work if the drive is mounted read-only; that is why I was reluctant to advise on that without having more information ;)

---

### Post by sudodus on 2013-01-03
> **Wim Sturkenboom said:**
> chown will not work if the drive is mounted read-only; that is why I was reluctant to advise on that without having more information ;)
That is right, let us wait for that information.

---

### Post by bman on 2013-01-03
When I did

```
sudo chown bman:bman Shows
```

It gave me

```
chown: cannot access `Shows': No such file or directory
```

Now is that because Wim is correct about it being read-only, or is that just the wrong thing to put?

That is the right code for the drive, and not a folder inside the drive called Shows right? 

Like I am saying it's not suppose to be

```
sudo chown bman:bman
``` while inside /media/Shows

Which I just tried and didn't work of course.

---

### Post by bman on 2013-01-03
> **Wim Sturkenboom said:**
> Where do you right click on the drives? I simply don't know what you mean by that and it confuses me a bit.
How do you mount them? Using /etc/fstab? If so, post the result of _cat /etc/fstab_. Or do you just double click them under devices in Nautilus?
How did you copy the files? Using sudo?

More questions than answers ;)

This is my setup for an ext3 partition (/dev/sdc1) that is mounted on startup under /mnt/photos
```

wim@i3-2120:~$ **[COLOR="Red"]ls -ld /mnt[/COLOR]**
drwxr-xr-x 4 root root 4096 Sep 16 18:28 /mnt
wim@i3-2120:~$ **[COLOR="Red"]ls -l /mnt[/COLOR]**
total 8
drwxr-xr-x 9 root root 4096 Sep 12 18:00 boot-sav
[COLOR="Red"]drwxr-xr-x 6 root root 4096 Dec 22  2010 photos[/COLOR]
wim@i3-2120:~$ 

```
My /etc/fstab is shown below
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=2e61cbc5-d982-4ada-8af7-cbdea09bb295 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0a1c5d63-223f-4dc3-9ab8-46f566f5fa7b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=15274769-0777-4a8e-a167-ec7501f8665a none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=0173d67a-bb5c-43bf-91c8-1fe03c5ff641 none            swap    sw              0       0

# photos (/dev/sdc1)
[COLOR="Red"]UUID="6ff7017c-e4d9-49ba-9a1b-b62e45dab820" /mnt/photos ext3 defaults 0 2[/COLOR]

```
And I have a shortcut on my desktop for easy access
```

wim@i3-2120:~$ **[COLOR="Red"]ls -l Desktop/[/COLOR]**
total 0
lrwxrwxrwx 1 wim wim 12 Sep 16 19:35 photos -> /mnt/photos/
wim@i3-2120:~$ 

```

Note 1:
You need to adjust this information to your needs; uuid will be different, filesystem is different etc

Note 2:
posted at 8:00 am so you have an idea of the time difference in case you still want me to help you remotely

And the reason I am not really trying to follow your information is because it's hard for me to understand, and it's your information as well, which makes it harder.

I am quite new to all of this. Also, I just tried fiddling with that stuff and that is how I messed it all up.

I also, do not want to make a shortcut on the desktop. Everything I am talking about is about Nautilus.

I did the first part of your code.

```
bman@T1000:~$ ls -ld /media
drwxr-xr-x 3 root root 4096 Jan  2 19:27 /media
bman@T1000:~$ ls -l /media
total 4
drwxr-xr-x 108 root root 4096 Jan  2 11:23 Shows
```

---

### Post by sudodus on 2013-01-03
Post the output of ```
cat /etc/mtab
``` to show how it is mounted. (rw means read/write, ro means read only)

And to be sure, maybe you should have the full path. I think it might work like this to change the ownership

```
sudo chown bman:bman /media/Shows
```

---

### Post by bman on 2013-01-03
```
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/bman/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=bman 0 0
/dev/sda1 /media/Shows ext4 rw,nosuid,nodev,uhelper=udisks 0 0
```

I did the full path and it didn't give me an error, but didn't do anything either.

After a small bit i double checked, and the drive is now Owned by me (bman) and Group is me (bman)

But everything inside the drive is still under root.

Would doing this work for all files under the drive?

```
chown -R bman:bman /media/Shows
```

---

### Post by sudodus on 2013-01-03
> **bman said:**
> ```

/dev/sda1 /media/Shows ext4 [COLOR="Red"]rw[/COLOR],nosuid,nodev,uhelper=udisks 0 0
```

I did the full path and it didn't give me an error, but didn't do anything either.

After a small bit i double checked, and the drive is now Owned by me (bman) and Group is me (bman)

But everything inside the drive is still under root.

Would doing this work for all files under the drive?

```
chown -R bman:bman /media/Shows
```
Yes, this is the next step. I didn't know you had already written files to it. 

In the future, when you write files (with your normal user id), they should be owned by you, and you should get proper permissions.

---

### Post by bman on 2013-01-03
Yea I figured when I create new files to those drives the permissions will be fine, these are because they were already there.

I did that command, and some of the files/folders are still locked, permissions say its me now, but i still can't change.

Maybe a restart?

I restarted but made no difference. Makes no sense, why are some folder unlocked and others not. They are all Owned and Grouped by me now, but only some of unlocked?

---

### Post by sudodus on 2013-01-03
> **bman said:**
> Yea I figured when I create new files to those drives the permissions will be fine, these are because they were already there.

I did that command, and some of the files/folders are still locked, permissions say its me now, but i still can't change.

Maybe a restart?

I restarted but made no difference. Makes no sense, why are some folder unlocked and others not. They are all Owned and Grouped by me now, but only some of unlocked?

Did you run chown -R with superuser privileges?

```
sudo chown -R bman:bman /media/Shows
```

Check the permissions: You might need to change them too, with a similar command ***chmod***. Read ```
man chmod
``` to learn about it. What permissions are good? Post the output of ```
ls -l
``` where you can point to some files with good permissions (such as you want), and I can suggest what options to use for chmod.

---

### Post by bman on 2013-01-03
Please ignore the folder names :)

```

dr-xr-xr-x 3 bman bman  4096 Jan  2 10:39 Alcatraz
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:44 Alphas
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:45 American Dad
drwxr-xr-x 3 bman bman  4096 Jan  2 10:48 Anger Management
drwxr-xr-x 3 bman bman  4096 Jan  2 10:52 Arrow
drwxr-xr-x 3 bman bman  4096 Jan  2 10:52 Awake
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:46 Being Human
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:46 Being Human (US)
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:48 Big Bang Theory
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:50 Boardwalk Empire
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:53 Bones
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:53 Bored to Death
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:56 Breaking Bad
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:56 Breaking In
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:56 Breakout Kings
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:56 Camelot
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:56 Caprica
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:58 Castle
dr-xr-xr-x 3 bman bman  4096 Jan  2 00:58 Chuck
drwxr-xr-x 3 bman bman  4096 Jan  2 01:00 Comic Book Men
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:00 Community
drwxr-xr-x 3 bman bman  4096 Jan  2 01:03 Continuum
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:03 Cougar Town
drwxr-xr-x 3 bman bman  4096 Jan  2 01:03 Death Valley
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:07 Dexter
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:09 Doctor Who
drwxr-xr-x 3 bman bman  4096 Jan  2 01:12 Dont Trust the Bitch in Apartment 23
drwxr-xr-x 3 bman bman  4096 Jan  2 01:16 Elementary
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:16 Entourage
drwxr-xr-x 2 bman bman  4096 Jan  2 01:16 Episodes
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:16 Eureka
drwxr-xr-x 3 bman bman  4096 Jan  2 01:16 Falling Skies
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:17 Family Guy
drwxr-xr-x 3 bman bman  4096 Jan  2 01:17 Friends With Benefits
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:20 Fringe
drwxr-xr-x 3 bman bman  4096 Jan  2 01:20 Frozen Planet
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:22 Futurama
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:22 Game of Thrones
drwxr-xr-x 3 bman bman  4096 Jan  2 01:24 Girls
drwxr-xr-x 3 bman bman  4096 Jan  2 01:26 Go On
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:29 Gossip Girl
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:33 Grimm
drwxr-xr-x 3 bman bman  4096 Jan  2 01:35 Guys With Kids
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:36 Happy Endings
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:40 Haven
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:40 House
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:43 How I Met Your Mother
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:43 Human Target
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:45 Its Always Sunny In Philadelphia
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:45 Justified
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:47 Last Man Standing
drwxr-xr-x 3 bman bman  4096 Jan  2 01:50 Longmire
drwx------ 2 bman bman 16384 Jan  1 19:38 lost+found
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:50 Lost Girl
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:54 Luther
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:54 Mad Men
drwxr-xr-x 3 bman bman  4096 Jan  2 01:57 Magic City
dr-xr-xr-x 3 bman bman  4096 Jan  2 01:59 Misfits
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:01 Modern Family
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:03 New Girl
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:05 Nikita
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:05 Nip Tuck
drwxr-xr-x 3 bman bman  4096 Jan  2 02:09 Once Upon A Time
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:09 One Tree Hill
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:09 Pan Am
dr-xr-xr-x 5 bman bman  4096 Jan  2 02:18 Parenthood
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:27 Person of Interest
drwxr-xr-x 2 bman bman  4096 Jan  2 02:27 Pretty Little Liars
drwxr-xr-x 2 bman bman  4096 Jan  2 00:48 $RECYCLE.BIN
dr-xr-xr-x 3 bman bman  4096 Jan  2 02:27 Revenge
drwxr-xr-x 3 bman bman  4096 Jan  2 02:31 Revolution
drwxr-xr-x 5 bman bman  4096 Jan  2 03:20 Rips
dr-xr-xr-x 3 bman bman  4096 Jan  2 03:46 Sanctuary
drwxr-xr-x 3 bman bman  4096 Jan  2 12:41 Saving Hope
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:57 Sherlock
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:57 **** My Dad Says
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:58 Skins
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:58 Smallville
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:58 Spartacus Blood and Sand
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:01 Stargate Universe
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:01 Star Wars The Clone Wars
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:02 Suburgatory
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:06 Teen Wolf
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:06 Terra Nova
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:06 The Borgias
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:07 The Cleveland Show
drwxr-xr-x 3 bman bman  4096 Jan  2 11:07 The Finder
dr-xr-xr-x 2 bman bman  4096 Jan  2 11:07 The IT Crowd (2008)
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:08 The Killing
drwxr-xr-x 3 bman bman  4096 Jan  2 11:11 The Legend Of Korra
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:15 The Mentalist
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:18 The Office
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:18 The Secret Circle
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:19 The Simpsons
dr-xr-xr-x 3 bman bman  4096 Jan  2 11:23 The Vampire Diaries
dr-xr-xr-x 4 bman bman  4096 Jan  2 11:27 The Walking Dead
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:16 Torchwood
drwxr-xr-x 3 bman bman  4096 Jan  2 10:21 Touch
drwxr-xr-x 3 bman bman  4096 Jan  2 10:23 Tron Uprising
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:23 True Blood
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:26 Two & A Half Men
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:29 Warehouse 13
drwxr-xr-x 2 bman bman  4096 Jan  2 10:32 Wedding Band
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:36 Weeds
dr-xr-xr-x 3 bman bman  4096 Jan  2 10:39 Wilfred (US)
drwxr-xr-x 2 bman bman  4096 Jan  2 10:39 Workaholics

```

As you can seem some are good, some are still not allowing me to change them.

And are you referring to a command like this.

```
chmod -R 755 /media/Shows
```

I just did that code, and all files and folders under the drive are editable/changable now.

Either the original code just took awhile or that one I just wrote worked.


So I guess the next step would be, how do I add user plex to my group?

**except for one thing, I can't seem to cut and paste a file from my downloads into a folder on that drive, or to another place. I can delete them though lol

Like I can drag a file from my Downloads into that drive, but I can't right click copy/cut and then paste.

---

### Post by sudodus on 2013-01-03
> 
And are you referring to a command like this.

```
chmod -R 755 /media/Shows
```

I just did that code, and all files and folders under the drive are editable/changable now.

Either the original code just took awhile or that one I just wrote worked.

So I guess the next step would be, how do I add user plex to my group?

**except for one thing, I can't seem to cut and paste a file from my downloads into a folder on that drive, or to another place. I can delete them though lol

Like I can drag a file from my Downloads into that drive, but I can't right click copy/cut and then paste.

Yes, that command with 755 means
read,write,execute for the user
read,,execute for group members
read,,execute for others

It may take time if there are many files, but when it returns to prompt in the terminal window, it should have finished.

I see that your subdirectories have execute permissions. Write and delete are governed by the same permission bit, 'write'. So you should be able to both write and delete in directories with write access. But only you, not group members, not others. If there is some individual file that is read-only, that file cannot be overwritten or deleted.

*Edit*: So you might consider using 775 instead of 755, to give group members write permission.
--
But were you allowed to ***read*** the file you wanted to cut and paste?

- How did you cut and paste?

- Can you test with terminal commands:

```
echo hello > /media/Shows/hello.txt
```

should write a file containing 'hello' with the file name 'hello.txt' in the directory '/media/Shows'

The next step is to copy a file from somewhere else with the cp command

```
cp source-file /media/Shows
``` should copy the file 'source-file' to the directory '/media/Shows' (keeping the basename).

You edit the group membership with the GUI tool ***Users and Groups*** or edit the file [FONT="Courier New"][SIZE="3"]/etc/group[/SIZE][/FONT] with a text editor. It is probably safer to use the GUI tool.

---

### Post by bman on 2013-01-03
I can open and read all files on the drive.

I can delete all files/folders on the drive.

I can rename all files/folders on the drive.

I can not copy/cut from or to the drive, inside Nautilus with the right click options. I can though, drag to or from the drive any files or folders.

See the screenshot, File Access is --, and I can't change it. Folders are all good.

***So the reason I am saying I can't cut/copy and paste is because the Paste button on the right click menu is greyed out, I randomly hit the paste button anyways, and it actually works, pastes the file anywhere I want without issue. So why is it greyed out then?

---

### Post by sudodus on 2013-01-03
> **bman said:**
> See the screenshot, File Access is --, and I can't change it. Folders are all good.

***So the reason I am saying I can't cut/copy and paste is because the Paste button on the right click menu is greyed out, I randomly hit the paste button anyways, and it actually works, pastes the file anywhere I want without issue. So why is it greyed out then?

1. I think you have marked a directory. If you mark a file (set the high-light bar on a file), you will get the typical operations and properties for files.

2. You must have something to paste, so cut or copy a file (to the clipboard), then you will have something to paste, and the paste option will not be greyed out.

---

### Post by bman on 2013-01-03
> **sudodus said:**
> 1. I think you have marked a directory. If you mark a file (set the high-light bar on a file), you will get the typical operations and properties for files.

2. You must have something to paste, so cut or copy a file (to the clipboard), then you will have something to paste, and the paste option will not be greyed out.

I am not sure what you mean by the first part, by marked?

And yes, that is what I mean. I cut and copied a file, but the paste option is still greyed out, but working. Weird right?

Anyway, it's pretty much working how I want it.

So how do I add plex to my group? (I haven't installed Plex yet) But based off there website, it becomes a user, plex.

---

### Post by sudodus on 2013-01-03
> **bman said:**
> I am not sure what you mean by the first part, by marked?

And yes, that is what I mean. I cut and copied a file, but the paste option is still greyed out, but working. Weird right?

That you select it, high-light it, show that you are interested in that particular file or directory. It is shown graphically with a different colour.

It works, that the important thing :KS If it is greyed out although it works, might be a small bug ;-)

---

### Post by bman on 2013-01-03
I think you missed my edit,

So how do I now add Plex Media Server to my group? I think it would be user named plex.

Also,

So to recap.

Best to have drives formatted as ext4 (or any other ext)

Open the directory that you want to change permissions in terminal and then run this command.

```
sudo chown -R bman:bman /media/Shows
```

then run this command 

```
sudo chmod -R 775 /media/Shows
```

---

### Post by sudodus on 2013-01-03
> **bman said:**
> I think you missed my edit,

So how do I now add Plex Media Server to my group? I think it would be user named plex.

Also,

So to recap.

Best to have drives formatted as ext4 (or any other ext)

Open the directory that you want to change permissions in terminal and then run this command.

```
sudo chown -R bman:bman /media/Shows
```

then run this command 

```
sudo chmod -R 775 /media/Shows
```

I wrote this reply to that question some time ago at the end of post #35

> You edit the group membership with the GUI tool ***Users and Groups*** or edit the file [FONT="Courier New"][SIZE="3"]/etc/group[/SIZE][/FONT] with a text editor. It is probably safer to use the GUI tool.

Can you find ***Users and Groups***?
--
Good summary :KS

---

### Post by bman on 2013-01-03
Is Users & Groups another program? Because I can't find any application called that.

Or when right clicking on the directory?

**I installed plex, started it up. Added the directory, and it found and is working 100%.

So it looks like what I did worked out.

---

### Post by bman on 2013-01-03
I just want to thank you sudodus and Wim for all the help. If I had money I would pay you for your services :)

This has actually been the best experience I have ever had on forums. I will be adding in the rest of my drives and following the instructions we just went through, so should be easy.

Thanks again :)

---

### Post by sudodus on 2013-01-03
> **bman said:**
> Is Users & Groups another program? Because I can't find any application called that.

Or when right clicking on the directory?
Since I use non-English menus, I translate the name I see, and sometimes the name in English is quite different, which causes confusion.

Anyway, the terminal command is
```
users-admin
``` Try that, it should be independent of the language of the menus.

*Edit*: Great, I'm happy to help. And it is very good that you stay until the end and share your results for the benefit of other forum members :KS

---

