---
title: "80GB IDE  Hard drive and an External HD Problem"
date: 2009-03-11
forum: Hardware
---

### Post by houseonfire on 2009-03-11
I have an 80GB HDD plugged into my motherboard through an IDE cable.
Power is plugged all the way in, the cable is plugged all the way in, and is not recognized by ubuntu at all.Not in the mount manager, or anything else I've tried. The drive is formatted.

I have an external hard drive plugged in via USB.
It is detected and everything, but I cannot do anything to it besides take files from it. I cannot make files, add files, or format the disk. fDisk doesn't let me, and chmod doesn't let me change its permissions. Any ideas?

Thanks.

---

### Post by taurus on 2009-03-11
1.  I assume you have set the jumper on the back of your second harddrive as slave if you connect it to the same ribbon with the first harddrive, PATA?  And the BIOS detects both properly?

Post the output of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

2.  What filesystem is your external harddrive, vfat or ntfs?

---

### Post by houseonfire on 2009-03-11
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c5d0c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x164d235c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15017   120624021    7  HPFS/NTFS

Disk /dev/sdf: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders
Units = cylinders of 20 * 512 = 10240 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          13       99200      991875+   6  FAT16

/dev/sda1: UUID="57dc476c-6859-4517-99f1-4084b539024d" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="2ea45bcf-d9e0-46e3-b0c5-b07337e61301" 
/dev/sdb1: UUID="0228366E283660B9" LABEL="External" TYPE="ntfs" 
/dev/sdf1: SEC_TYPE="msdos" LABEL="HP_M2X" UUID="5CF3-5F72" TYPE="vfat" 

/dev/scd0 /media/cdrom0 udf,iso9660 noauto 0 0
UUID=57dc476c-6859-4517-99f1-4084b539024d / ext3 defaults 0 1
UUID=2ea45bcf-d9e0-46e3-b0c5-b07337e61301 swap swap sw 0 0

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             450G  246G  181G  58% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  340K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  3.0M  2.0G   1% /dev
tmpfs                 2.0G  332K  2.0G   1% /dev/shm
/dev/sdb1             116G   82G   34G  71% /media/sdb1
/dev/scd0             4.4G  4.4G     0 100% /media/cdrom0
/dev/scd0             4.4G  4.4G     0 100% /media/sr0
/dev/sdf1             969M   69M  900M   8% /media/HP_M2X


My external is NTFS.

And I'll put a jumper on it now. I did'nt think it necessary.
Thanks.

I slipped a jumper into the slave slot on my 80gb drive (the only IDE anything plugged in) and it's not detected.

---

### Post by houseonfire on 2009-03-11
tim@tim-desktop:~$ sudo fdisk '/media/sdd1' 
last_lba(): I don't know how to handle files with mode 40777
You will not be able to write the partition table.

Unable to read /media/sdd1
tim@tim-desktop:~$ 

This pops up when I try to fdisk my external (115gb drive)

---

### Post by taurus on 2009-03-12
Go back into the BIOS to see if the BIOS even detects it.  If the BIOS doesn't detect your 80GB drive, no OS would.

---

