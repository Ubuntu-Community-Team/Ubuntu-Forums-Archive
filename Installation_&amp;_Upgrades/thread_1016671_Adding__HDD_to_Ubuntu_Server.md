---
title: "Adding  HDD to Ubuntu Server"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by falconed7 on 2008-12-20
Hey everyone!

I have installed 2 HDDs in my server build (Ubuntu Server 8.04.1) and using the "Guided - Use entire disk" option, I installed the OS onto the small 80GB. I have a feeling I should have done something else (ie. use "Manual" partition) as I think my 750GB (for data) is unformatted. Would this be right?

I was told that the installation would take care of the HDDs however, I chose guided due to not knowing what to do. 

I would like the disks like:
80GB = OS (Already installed using Guided)
750GB = Data (wanting it in ext3)

Am I right in saying that what I need to do now is format and mount the data HDD?

I'll post my fstab if it helps:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f0b9914d-5cc3-4d80-b6dd-23f5918fc932 /               ext3    relatime,erro$
# /dev/sda5
UUID=2f1c486b-6b1f-4e14-9b11-385aa558ada5 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Here is what I get with fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

So I believe I need to format my 750GB HDD and mount it. Can anyone point me in the right direction?

Cheers.

---

### Post by lovelyvik293 on 2008-12-20
Yes you have to format the hard disk.It may help you
[http://ubuntuforums.org/showthread.php?p=1594087](http://ubuntuforums.org/showthread.php?p=1594087)

---

### Post by falconed7 on 2008-12-20
> **lovelyvik293 said:**
> Yes you have to format the hard disk.It may help you
[http://ubuntuforums.org/showthread.php?p=1594087](http://ubuntuforums.org/showthread.php?p=1594087)

Thanks for the quick reply.

I see that is more directed at formatting a external HDD. Am I safe to assume that it's a similar method for internal SATA drives?

Also would I mount this drive to be "/home/user/..." or would I mount it as "/media/..."? I read that "/media/..." is used for removable storage.

---

### Post by lovelyvik293 on 2008-12-20
Yes you can format the internal HDD with this.
And you have the HDD2 at /dev/sdb.

---

### Post by logos34 on 2008-12-20
> **lovelyvik293 said:**
> Yes you have to format the hard disk.It may help you
[http://ubuntuforums.org/showthread.php?p=1594087](http://ubuntuforums.org/showthread.php?p=1594087)

Since that link only seems to cover formatting, here's how to edit fstab and permissisons so the drive automounts and is accessible to user(s):

[https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot](https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(-> bottom - re: chmod, chown, etc)

---

