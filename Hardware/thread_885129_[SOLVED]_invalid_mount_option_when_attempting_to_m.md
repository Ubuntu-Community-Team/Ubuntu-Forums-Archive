---
title: "[SOLVED] invalid mount option when attempting to mount the volume"
date: 2008-08-09
forum: Hardware
---

### Post by jybeard on 2008-08-09
I'm attempting to mount my Maxtor external hard drive and I am getting this error.

"invalid mount option when attempting to mount the volume"

Here is what I get when I type in 'mount'

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd2 on /media/U3 System Files type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdc1 on /media/TravelDrive type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
jybeard@Home1:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 1994 MB, 1994292736 bytes
4 heads, 16 sectors/track, 60860 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x7d7654d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60861     1947543+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ce28d3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192+   b  W95 FAT32
jybeard@Home1:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f82dec04-9c75-4269-a171-eb6b95a2569f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8d16a8e2-73c1-4b7f-8983-e40cf7726d8f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


I don't know what any of this means.  Plese help.

---

### Post by jybeard on 2008-08-09
Oh yeah,

Here is the fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f82dec04-9c75-4269-a171-eb6b95a2569f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8d16a8e2-73c1-4b7f-8983-e40cf7726d8f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by cdtech on 2008-08-09
Your trying to mount your "root" partition (sda1) which is already mounted. You need to plug in your external drive and type "sudo fdisk -l" on a command line and find out which device it shows as your external drive (probably /sdc). Then you can do a "mount /dev/sdc /media/external" if you create a directory under /media and call it "external" or whatever.

---

### Post by jybeard on 2008-08-09
After I typed fdisk -l here is the result

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

]Disk /dev/sdc: 1994 MB, 1994292736 bytes
4 heads, 16 sectors/track, 60860 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x7d7654d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60861     1947543+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ce28d3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192+   b  W95 FAT32




Then I typed in  

> mount /dev/sdc /media/external
mount: only root can do that


---

### Post by cdtech on 2008-08-09
It looks to me that the /dev/sdb is the external drive.

Try "sudo mount /dev/sdb1 /media/external"

---

### Post by Jordanwb on 2008-08-09
Nevermind cdtech beat me.

---

### Post by jybeard on 2008-08-09
Result:

> sudo mount /dev/sdc /media/external
mount: mount point /media/external does not exist

---

### Post by cdtech on 2008-08-09
Look at my post, I updated it to mount the sdb1 partition.....

Did you create a directory under /media named external?

---

### Post by jybeard on 2008-08-09
Please remember that I have information on that drive I don't want to lose.  I don't want to format it.

---

### Post by Jordanwb on 2008-08-09
He means make a directory in /media:

sudo mkdir /media/external

Well /dev/sdc won't work because you're trying to mount the whole drive and not the partiton:

sudo mount /dev/sdc1 /media/external

---

### Post by cdtech on 2008-08-09
That wont format it, only mount it to read from it.

---

### Post by jybeard on 2008-08-09
I think i just mounted the flash drive i have connected.

---

### Post by jybeard on 2008-08-09
My Maxtor drive did not mount.  When I look in the folder listed as 'external' I see information from my flash drive.

Please be patient with me, I'm pretty much still a beginner with Ubuntu.

---

### Post by cdtech on 2008-08-09
Yes I think you wanted to mount the /dev/sdb1 instead. Just do a "sudo umount /dev/sdc1" and then try with the sdb1.

---

### Post by cdtech on 2008-08-09
> **jybeard said:**
> My Maxtor drive did not mount.  When I look in the folder listed as 'external' I see information from my flash drive.

Please be patient with me, I'm pretty much still a beginner with Ubuntu.

No problem. Your almost there.:)

Just need to get the right device....

---

### Post by jybeard on 2008-08-09
I'm smilin from ear to ear.  Works!!!

Thank you!:)

---

### Post by cdtech on 2008-08-09
alright, congrats. :lolflag:

---

