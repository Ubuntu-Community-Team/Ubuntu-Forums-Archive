---
title: "convert exfat drive to ext3"
date: 2016-09-14
forum: Hardware
---

### Post by YaPaY on 2016-09-14
I have remote server which pluggedin a external hdd with exfat format

I live some problems about the permission so I decided to convert it ext3.

but 

if possible I would like to keep data and after convert I wont need to plug out plug in disk. Because it is in Datacenter and I havent got physically access to it

thanks a lot

---

### Post by TheFu on 2016-09-14
Don't know any in-place conversion method.

[LIST=1]
[*]Backup the data - refresh it.
[*]umount the partition.
[*]Format the partition to ext4.
[*]mount the partition.
[*]Restore the data to the newly formatted storage from the backup copy.
[/LIST]

Good thing you have that backup storage. It would be crazy NOT to have backups after all.  Just try to limit the amount of time the backup is the only copy.  Problems tend to happen when they are least expected.

---

### Post by YaPaY on 2016-09-15
Thanks for reply

The drive is usb and exfat when try the unmount getting this message

umount: /media/exfat: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

I am trying the kill the process which uses the hdd

lsof /dev/sdb1

lsof: WARNING: can't stat() fuseblk file system /media/exfat
      Output information may be incomplete.


any help?

---

### Post by YaPaY on 2016-09-15
a short edit. According to the format tutorials Ihave been deleted all 4 partition and make a new partition on hdd and enter: w

next step would be format but

mkfs.ext3 /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!


now what would be suggest me

---

### Post by TheFu on 2016-09-15
a) lsof needs sudo.
b) use **sudo lsof | grep  {path-to-directory}** - not the partition device to see which program(s) are keeping it busy.
c) you cannot format an active partition (i.e. mounted). Those steps AND THE ORDER are critical.

Please confirm that a backup to different storage has been made. If not, this will loose any data on the USB device.

Why ext3?  Use ext4 if you don't have a very good reason.

---

### Post by reese1379 on 2016-09-15
# get a list of processes accessing the device
#
fuser -m /dev/sdb1
#
# list what user is accessing the device
#
ps auxw|grep PID
#
# and kill them
#
kill -9 PID

---

### Post by YaPaY on 2016-09-15
> **TheFu said:**
> a) lsof needs sudo.
b) use **sudo lsof | grep  {path-to-directory}** - not the partition device to see which program(s) are keeping it busy.
c) you cannot format an active partition (i.e. mounted). Those steps AND THE ORDER are critical.

Please confirm that a backup to different storage has been made. If not, this will loose any data on the USB device.

Why ext3?  Use ext4 if you don't have a very good reason.

b) sudo lsof | grep sdb1 (not any output)

I confirm I backuped all the files and folder to another place. ext4 is ok, you are right

---

### Post by YaPaY on 2016-09-15
> **reese1379 said:**
> # get a list of processes accessing the device
#
fuser -m /dev/sdb1
#
# list what user is accessing the device
#
ps auxw|grep PID
#
# and kill them
#
kill -9 PID

fuser command gives no output
pps auxw|grep PID
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
yapay   22136  0.0  0.0  11752  2272 pts/0    S+   19:54   0:00 grep --color=auto PID
yapay@Trans2:~$ kill -9 22136
-bash: kill: (22136) - No such process

---

### Post by TheFu on 2016-09-15
ext4 is more than ok, it is preferred over ext2/3 - because it is faster than the others.

sdb1 is probably NOT the mount'd directory location.  Where is this mounted? That is what {path-to-directory} means.
For clarity - ```

$ df
Filesystem                         Size  Used Avail Use% Mounted on
/dev/sda5                           20G  2.6G   16G  14% /
/dev/mapper/vg--hadar-lv--hadar    388G  109G  259G  30% /var
/dev/mapper/vg--hadar-lv--backups  387G  317G   51G  87% /Backups
```

I'm using LVM, so don't have any easy-to-compare USB storage connected.  But for argument, lets say that /dev/mapper/vg--hadar-lv--hadar is /dev/sdb1 - so the mount point is /var - THAT is what needs to be in the lsof-grep cmd.

---

### Post by YaPaY on 2016-09-15
> **TheFu said:**
> ext4 is more than ok, it is preferred over ext2/3 - because it is faster than the others.

sdb1 is probably NOT the mount'd directory location.  Where is this mounted? That is what {path-to-directory} means.
For clarity - ```

$ df
Filesystem                         Size  Used Avail Use% Mounted on
/dev/sda5                           20G  2.6G   16G  14% /
/dev/mapper/vg--hadar-lv--hadar    388G  109G  259G  30% /var
/dev/mapper/vg--hadar-lv--backups  387G  317G   51G  87% /Backups
```

I'm using LVM, so don't have any easy-to-compare USB storage connected.  But for argument, lets say that /dev/mapper/vg--hadar-lv--hadar is /dev/sdb1 - so the mount point is /var - THAT is what needs to be in the lsof-grep cmd.

it is mounted the directory /media/exfat

```
yapay@Trans2:~$ sudo lsof | grep /media/exfat
[sudo] password for yapay:
yapay@Trans2:~$ sudo mkfs.ext4 /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
volkan@Transcode2:~$

```

---

### Post by TheFu on 2016-09-15
Try:
**$ sudo lsof | grep exfat**

If that doesn't show anything ... is it even mounted?  try **sudo umount /media/exfat**
If that doesn't work, shutdown the file manager, if being used. Is there a GUI running and gvfs doing something?

---

### Post by YaPaY on 2016-09-15
> **TheFu said:**
> Try:
**$ sudo lsof | grep exfat**

If that doesn't show anything ... is it even mounted?  try **sudo umount /media/exfat**
If that doesn't work, shutdown the file manager, if being used. Is there a GUI running and gvfs doing something?

```
sudo umount /media/exfat
umount: /media/exfat: not mounted

```

There is no FM or GUI, I am connecting via Putty

---

### Post by TheFu on 2016-09-15
Suspected that. Had to ask.

If no process is using the storage, yank it ... er ... or reboot the machine. I assume it isn't mounted through the /etc/fstab, right?  I don't see how it can be "in use" and not mounted too.

---

### Post by YaPaY on 2016-09-15
yes it seems single solution from my side is restart the server. I will do that at the midnight. I hope I hope I would not to plugout plugin the disk after reboot. It would makes really headache. I will inform you

---

### Post by TheFu on 2016-09-15
definitely pre-check the /etc/fstab to ensure no part of that drive will be mounted.

---

### Post by YaPaY on 2016-09-15
> **TheFu said:**
> definitely pre-check the /etc/fstab to ensure no part of that drive will be mounted.

I have no idae what you mean but it is the fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=3a58b835-675e-4ad3-8d03-3c56154a24f2 /               ext4    errors=remount-ro 0       1

```

---

### Post by TheFu on 2016-09-15
Whoa.  What is the device mapping to that, 3a58b835-675e-4ad3-8d03-3c56154a24f2, UUID?  xfat devices should have shorter UUIDs and according to you, not be ext4.   It is likely the sdb1 comment line isn't true anymore, so everything is fine.

---

### Post by YaPaY on 2016-09-16
I have been restarted the server

```
root@Trans2:~# mkfs.ext4 /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
61054976 inodes, 244190102 blocks
12209505 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

root@Trans2:~# fdisk -l

Disk /dev/sda: 293.6 GB, 293563949056 bytes
255 heads, 63 sectors/track, 35690 cylinders, total 573367088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ee22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   439169023   219583488   83  Linux
/dev/sda2       439171070   573366271    67097601    5  Extended
/dev/sda5       439171072   573366271    67097600   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204883968 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e6a4274

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1953522863   976760408    7  HPFS/NTFS/exFAT

```

fdisk -l hows up still sdb1 exfat

edit: fixed

thanks to help

---

### Post by TheFu on 2016-09-16
For a time, fdisk had issues with GPT partitions. I find it best just to avoid it and use either **parted** or **gparted** for partitioning. These tools also handle alignment issues. This way, I don't need to keep track of the fdisk versions that work and which don't. Don't think that is an issue with your stuff at all. Just passing on a little wisdom.

Did you mark the partition type as "linux" inside fdisk/parted/gparted?  Think is it 80 or 82, but don't quote me.

Besides that, looks like it worked.

These new-fagled Linux mounting tools like disks/partitions to be labeled. Might want to do that when you are back in.  Automatic mount locations are often based on labels.  No spaces. No funny characters are best for a few reasons, even if they are allowed.

---

