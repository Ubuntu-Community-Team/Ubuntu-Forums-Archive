---
title: "Problems mounting external USB drive to /home at boot time"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by to0om on 2008-01-25
Hello,

I'm trying to mount an external usb drive to /home automatically at boot time. Here's how I try to accomplish this (the lines I added to /etc/fstab):

```

# /dev/sda6
UUID=daaaac59-10c4-4ead-ab3f-f0b2e06134f2 /home           ext3    defaults        0       2
```

But there are a few problems with it. When i boot the system with these lines added to fstab, the bootup process suddenly stops and gives me these errors:

```
Checking file systems...
[...]
fsck.ext3: Unable to resolve 'UUID=5ccbe117-6b8a-466c-93de-01dc86910731'
fsck died with status 8

* File system check failed
```

I double-checked the UUID and I also tried to address the partition with */dev/sdb1* and */dev/disk/by-label/thomas*, but these gave me similiar errors (all of them pointing out that the drive just isn't available at that time).

When this error occurs, Ubuntu starts a Maintenance shell. In that shell, i tried to check the file system of the usb drive with fsck.ext3, and the program didn't display any errors! So a few seconds later, the drive was suddenly available. Moreover, after exiting the maintenance shell with Ctrl-D, the drive was correctly mounted! So the line specified in fstab is obviously correct.

I don't know how to try it any more. I have also tried to set the 'pass' option in fstab to 0 (so that it isn't checked at bootup), but then the drive isn't even mounted. I also set the option 'auto', so that it is mounted automatically at boot. Executing ```
sudo mount -a
``` when the system has finished booting works fine, the external drive is correctly mounted to /home.

I guess the problem is that it's a USB drive. All other drives specified in fstab mount flawlessly.

Can anyone give me an advice? Any help is very much apprechiated.

Thanks,

Tom

---

### Post by taurus on 2008-01-25
Are there other partitions on that external harddrive?  Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by to0om on 2008-01-25
Hello,

yes, there's another NTFS partition on the drive.

this is the output of fdisk -l:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4845    38917431    7  HPFS/NTFS
/dev/sda2            4846       14593    78300810    5  Extended
/dev/sda5            4846        6892    16442496   83  Linux
/dev/sda6            6893       13676    54492448+  83  Linux
/dev/sda7           14332       14580     2000061   82  Linux swap / Solaris
/dev/sda8           14581       14593      104391    b  W95 FAT32
/dev/sda9           13677       14229     4441941   83  Linux
/dev/sda10          14230       14331      819283+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37608   302086228+  83  Linux
/dev/sdb2           37609       38913    10482412+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006c394

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux
```

And here my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=98c0a62c-cba3-493b-9f6f-79ebb575c39f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
/dev/sdb1 /home           ext3    defaults        0      0000000000
# /dev/sda6
UUID=daaaac59-10c4-4ead-ab3f-f0b2e06134f2 /home2           ext3    defaults        0       2
# /dev/sda1
UUID=3490D3F290D3B916 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=4666-A970  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=ce3ffd5e-8577-4f6d-ac94-1762d6563f01 /media/sda9     ext3    defaults        0       2
# /dev/sda7
UUID=f22bf1f1-32e6-4fe3-9a08-14958af2c4eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

df -h:

```
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda5              16G  4,5G   11G  31% /
varrun               1014M  320K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  128K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6              52G   37G   13G  75% /home
/dev/sda1              38G   14G   24G  37% /media/sda1
/dev/sda8             101M   38K  101M   1% /media/sda8
/dev/sda9             4,2G  3,2G  828M  80% /media/sda9
/dev/sdc1             294G  238G   42G  86% /media/disk
/dev/sdb1             284G  246G   27G  91% /media/thomas
```

I have to say that the partition is mounted at /media/thomas at this time.

Thanks,

Tom

---

### Post by taurus on 2008-01-25
What partition is your /home?  I see that you tried to mount /dev/sda6 and /dev/sdb1! 

As of right now, you have /dev/sda6 mounted to /home while /dev/sdb1 mounted to /media/thomas.

---

### Post by to0om on 2008-01-25
As I said, this is the state of *now*. As I'm unable to mount the external USB device at boot time, i mountet an internal partition in the meantime. That's why /dev/sda6 is mountet to /home instead of /dev/sdb1 for now. /media/thomas is the path that KDE chooses to mount the drive at.

---

