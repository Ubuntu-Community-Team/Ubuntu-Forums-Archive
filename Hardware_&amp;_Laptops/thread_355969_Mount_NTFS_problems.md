---
title: "Mount NTFS problems"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by aversin on 2007-02-07
I can't seem to get my 120 GB drive to mount. Any ideas?

Here is my fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14592   117210208+   7  HPFS/NTFS


Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=5b4aca0d-2c66-42d1-81ee-dd8321e43278 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=afd2c0d1-99df-4b5d-b21e-bd32e09a4a11 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto      0       0
/dev/hdd        /media/stuff    ntfs nls=utf8,unmask=0222   0       0

I have made the /media/stuff directory.  *I'm slow not completly dumd*

Here is where is starts to go bad....

aver@aver-desktop:~$ sudo mount /dev/hdd
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

aver@aver-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any ideas? Did I fat finger something?

Thanks in advance for your help.

---

### Post by meng on 2007-02-07
You're very close. Look at this:
> /dev/hdd /media/stuff ntfs nls=utf8,unmask=0222 0 0
The first part should read /dev/hdd1
/dev/hdd is a DRIVE
/dev/hdd1 is a PARTITION (on that drive)

---

### Post by raul_ on 2007-02-07
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

;)

---

### Post by aversin on 2007-02-07
I still get the same error message. 

I tried hdd1 before posted. 

I try not to be one of those guys who when it dosen't work the first time comes here expecting answers. 

I am out of new ideas.

---

### Post by meng on 2007-02-07
Oh, also note that it's umask not unmask. Possibly this correction may solve your problem.

By the way, it's quite clear that you're not the "post a thread at the first sign of trouble" type of user. Kudos!

---

### Post by aversin on 2007-02-07
Dang....I can't believe I missed that.

Good catch, and thanks

---

### Post by meng on 2007-02-07
> **aversin said:**
> Dang....I can't believe I missed that.
Well I missed it too, so don't be feeling too bad. Hope it helps.

---

### Post by TheRealEdwin on 2007-02-08
Is it kosher to ask for assistance with my NTFS mounting issues in someone else's thread, or should I just start my own? I've had other users check out my fstab as well and I was hoping for a fresh eye on this.

---

