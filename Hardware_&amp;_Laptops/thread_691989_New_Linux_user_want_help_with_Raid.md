---
title: "New Linux user want help with Raid"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by ruckstande on 2008-02-09
Hello, I have just installed Linux onto my Asus K8V-SE Deluxe computer and love it. Here is my dilemma though. I have 4 HDD on my computer two hard drives are using VIA VT8237 SATA which hosts my Windows XP Pro installation, the second drive is a spare Sata drive for storing TV media, and the 3rd is a 120 gb IDE drive which hosts my Ubuntu installation. Currently Ubuntu doesn't list the drives with the Raid installation of Windows. Is it possible to access the Raid array without hurting the Windows installation?
I found Via Raid drivers here. [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=143)
Thanks ahead of time.

---

### Post by jan quark on 2008-02-09
hey ruckstande

well don't know exactly about raid but we can look if the drives are recognized by ubuntu in the first place

I hope you have successfully installed the drivers from the link posted above :)

so let's see what we have 

run these commands and post the output please
```

mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by jan quark on 2008-02-09
please send me a short PM (private message) when you have replied 
thank you

---

### Post by ruckstande on 2008-02-09
> **jan quark said:**
> hey ruckstande

well don't know exactly about raid but we can look if the drives are recognized by ubuntu in the first place

I hope you have successfully installed the drivers from the link posted above :)

so let's see what we have 

run these commands and post the output please
```

mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```
> mount

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdd1 on /media/My Book type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


> sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41b70198

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x6697 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00f5d360

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       60801   457667752+   f  W95 Ext'd (LBA)
/dev/sdb5   ?       46652      238829  1543664152+  3f  Unknown

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02660100

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x681179e9

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13995   112414806   83  Linux
/dev/hda2           13996       14593     4803435    5  Extended
/dev/hda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1be5bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38912   312560608+   7  HPFS/NTFS

> cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c06cc36e-9d26-4c61-8f58-8fef7436c536 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=df3179d9-0e4b-4e6f-b69d-aab1686f9386 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by ruckstande on 2008-02-11
Okay I downloaded the drivers from VIA and I couldn't figure out what to do with them. Like I said I'm new to Linux and pretty ignorant. I have a long way to go.

---

