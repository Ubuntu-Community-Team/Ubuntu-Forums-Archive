---
title: "second HDD?"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by Shinobi_no_mono on 2007-08-28
I installed another HD on my Edgy box today, but I can't seem to find where it is. Does anyone know where it would be located or if I have to configure something in Ubuntu for it to appear so I can move files to it? Its listed in the bios and also under "device manager" yet I don't see it listed in "computer". :(

any help appreciated,
thanks!

---

### Post by merlinus on 2007-08-28
Look in file system/media.

-merlin

---

### Post by Shinobi_no_mono on 2007-08-28
> **merlinus said:**
> Look in file system/media.

-merlin

Just cdrom, cdromo and floppy and floppy0 listed in there.

---

### Post by merlinus on 2007-08-28
Post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

### Post by Shinobi_no_mono on 2007-08-28
> **merlinus said:**
> Post results of:
```

sudo fdisk -l
mount
cat /etc/fstab

```
-merlin

[QUOTE=sudo fdisk -l]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60139   483066486   83  Linux
/dev/sda2           60140       60801     5317515    5  Extended
/dev/sda5           60140       60801     5317483+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
[/QUOTE]

[QUOTE=mount]
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-12-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
[/QUOTE]

[QUOTE=cat /etc/fstab]
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1f1e0b48-5a92-4cd7-a04a-594597b6e179 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d73a7d92-8837-4420-9c95-d1cef167f11a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[/QUOTE]

Seems its not formatted is that the case?
THANKS!

---

### Post by merlinus on 2007-08-28
You are correct.  Once formatted, it may then show up.

-merlin

---

### Post by Shinobi_no_mono on 2007-08-28
> **merlinus said:**
> You are correct.  Once formatted, it may then show up.

-merlin

How would I go about formatting a drive that doesn't show up in Ubuntu?

Sorry I'm still a newbie and only know how on Windoze!

---

### Post by merlinus on 2007-08-28
You can format it as NTFS in windows, and then install drivers so ubuntu can write to it.

-merlin

---

### Post by Shinobi_no_mono on 2007-08-28
> **merlinus said:**
> You can format it as NTFS in windows, and then install drivers so ubuntu can write to it.

-merlin

Is there a "non-Windoze" way to do it? I don't want to swap it out and into the older pc at all, should be a way to do it without any MS involvement.

---

### Post by merlinus on 2007-08-28
Try this:

    ```

     sudo fdisk /dev/sdb 

```If that is successful, then

    ```

     sudo mkfs -t ext3 /sdb1 

```-merlin

---

### Post by Shinobi_no_mono on 2007-08-28
> **merlinus said:**
> Try this:

    ```

     sudo fdisk /dev/sdb 

```If that is successful, then

-merlin

I got this :(

> 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 91201.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)


A friend of mine recommended to install Gnome Partition Editor wherever that is!

---

### Post by merlinus on 2007-08-28
You can use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

