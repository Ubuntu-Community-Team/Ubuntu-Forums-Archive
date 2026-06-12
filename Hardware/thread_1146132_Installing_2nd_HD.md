---
title: "Installing 2nd HD"
date: 2009-05-02
forum: Hardware
---

### Post by dafydd_brown on 2009-05-02
Hi. I followed the instructions on [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) to install a second hard drive. Things seemed to be going well but now it's telling me I that I'm "not Priveleged to mount this volume".  Also it's telling me that "mount point /media/storage/" does not exist.

I partitioned it using GParted to fill the whole disk space and chose FAT 32 as the formatting. Then I tried to mount it following instructions on the same page.
I don't know if it was a stupid thing to do or not but I deviated slightly from the instructions as I thought that the following instruction labelled the drive as 'mynewdrive' and I wanted to call it 'Storage' instead. E.g.
sudo mkdir /media/storage

I then opened etc/fstab and added the following line to the end:
/dev/sdb1    /media/storage   vfat    defaults     0        2

Then I did the following as it seemed like what I wanted 
although I'm wondering if given the problems, this is where I went wrong.
sudo chown -R username:username /media/storageOn rebooting the mounting of the drive also suggests that the mountpoint does not exist.
Any help would be appreciated!

*edit*
When trying to manually mount the drive (again following instructions from link at beginning of thread post), I'm told "mount: can't find /dev/sdb1/media/storage in /etc/fstab or /etc/mtab" although the entry i place in etc/fstab is clearly there... and as instructed.

---

### Post by taurus on 2009-05-02
What's the output of this command from a terminal?

```
ls -la /media
```
Also, you should modify the entry in /etc/fstab for your second harddrive to make it look something like this.

```
/dev/sdb1 /media/storage vfat **iocharset=utf8,umask=000 0 0**
```

p.s.  Post the output of this command too.

```
sudo fdisk -l
```

---

### Post by dafydd_brown on 2009-05-02
Hi, thanks for the quick reply.
Output from ls -la /media is:
total 24
drwxr-xr-x  6 dafydd dafydd 4096 2009-05-02 15:16 .
drwxr-xr-x 21 root   root   4096 2009-05-02 12:03 ..
lrwxrwxrwx  1 dafydd dafydd    6 2009-04-26 19:20 cdrom -> cdrom0
drwxr-xr-x  2 dafydd dafydd 4096 2009-04-26 19:20 cdrom0
-rw-r--r--  1 root   root      0 2009-05-02 15:14 .hal-mtab
drwxr-xr-x  2 root   root   4096 2009-05-02 14:51 sdb1
drwxr-xr-x  2 root   root   4096 2009-05-02 15:16 storage
drwxr-xr-x  2 dafydd dafydd 4096 2009-05-02 14:35 Storage

I've changed the fstab as suggested - any way I can I can test this?

THe output for sudo fdisk -1 is:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by taurus on 2009-05-02
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

What happens if you try to mount it again with

```
sudo mount -a
df -h
```

---

### Post by dafydd_brown on 2009-05-02
D'oh! I can't tell the difference between digits and numbers now... lol.

fdisk -l is:
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddf93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4863     1477980    5  Extended
/dev/sda5            4680        4863     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ae315

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32

result of mount -a is:
[mntent]: line 10 in /etc/fstab is bad

result of df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.6G   30G  11% /
varrun                248M  100K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   56K  248M   1% /dev
devshm                248M   12K  248M   1% /dev/shm
lrm                   248M   40M  208M  16% /lib/modules/2.6.24-23-386/volatile

---

### Post by taurus on 2009-05-02
Post the whole content of /etc/fstab.

```
cat /etc/fstab
```

---

### Post by dafydd_brown on 2009-05-02
I don't think I entered your changes for fstab properly sorry. This is what I now get from sudo fdisk -l:
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddf93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4863     1477980    5  Extended
/dev/sda5            4680        4863     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ae315

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32

Do you still want the whole contents of fstab?
Thanks for your help so far, it's much appreciated.

---

### Post by taurus on 2009-05-02
There is something wrong with your /etc/fstab, line 10, so yes, I need to see it to figure out what's wrong with it.  Probably a syntax error when you entered an entry to mount your second harddrive.

---

### Post by dafydd_brown on 2009-05-02
[FONT=monospace]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=ec425043-b298-40d7-b817-8c6fc93c8963 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=d0ce3e1c-401a-4ecb-a825-ac760f21de30 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 /media/storage vfat iocharset=ut f8, unmask=000 0 0

[/FONT]

---

### Post by taurus on 2009-05-02
> **dafydd_brown said:**
> [FONT=monospace]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=ec425043-b298-40d7-b817-8c6fc93c8963 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=d0ce3e1c-401a-4ecb-a825-ac760f21de30 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
**[COLOR="Red"]/dev/sdb1 /media/storage vfat iocharset=ut f8, unmask=000 0 0[/COLOR]**

[/FONT]

You have a couple of extra spaces and a typo.

```

/dev/sdb1  /media/storage  vfat  iocharset=utf8,umask=000  0  0

```

---

### Post by dafydd_brown on 2009-05-02
Brilliant! Thanks for your patience. I seem to have access now... is there anything else I need to do in order to use the drive?
Would it be a bother to explain what you've shown me to do or do you have a link? Failing that, what was wrong with the line I originally had in fstab i.e. 
/dev/sdb1    /media/storage   vfat    defaults     0        2
Thanks again.

---

### Post by taurus on 2009-05-02
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

