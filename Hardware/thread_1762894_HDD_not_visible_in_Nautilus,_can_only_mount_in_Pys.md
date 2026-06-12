---
title: "HDD not visible in Nautilus, can only mount in Pysdm, can't auto mount"
date: 2011-05-19
forum: Hardware
---

### Post by flatline403 on 2011-05-19
I'd very much appreciate any help with this, spent several hours on it and couldn't find a similar problem anywhere else.

Ubuntu 10.04. Desktop PC has 3 internal SATA drives:
Seagate 200GB (Ubuntu root and swap, plus empty FAT32 partition)
Samsung 2TB NTFS (works perfectly, automatically mounts on boot)
**WD Green 2TB NTFS -Drive with the issue.**

After installing 10.04, my 2TB Samsung NTFS drive has shown up on the left in Nautilus, exactly as it should.
My 2TB WD Green NTFS drive does not show up at all.
[IMG]http://www.mareundarum.com/naut2.png[/IMG]



I am able to mount the drive using Pysdm, but I have to do it every time I reboot.   I need it to mount automatically because I need a SAMBA share on this drive.
[IMG]http://www.mareundarum.com/pysdm.png[/IMG]


The WD drive also does not show up under gvfs:
```

manuel@Natalie:~$ gvfs-mount -l
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(1): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
Drive(2): 2.0 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): SMSNG 2TB MOVIES MAIN
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
manuel@Natalie:~$

```The WD drive does show up on blkid:
```

manuel@Natalie:~$ blkid
/dev/sda1: UUID="786c870c-b0f1-4e6b-a5ee-4fd63c88a300" TYPE="ext4"
/dev/sda3: UUID="D978-3B2C" TYPE="vfat"
/dev/sda5: UUID="da8bbd1f-a2bf-4a0b-875e-d383a88f7111" TYPE="swap"
**/dev/sdb1: LABEL="WD2TB_TV" UUID="2AB88F39B88F0315" TYPE="ntfs"**
/dev/sdc1: LABEL="SMSNG 2TB MOVIES MAIN" UUID="68B04048B0401EC6" TYPE="ntfs"

```My Entire fstab.  Note that I have tried hard-coding the UUID of the problem drive.  Ubuntu stalls on boot up and tells me that "The disk drive for /media/WD2TB is not ready yet or not present. S to Skip or continue waiting" -and I hit S to skip.

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid    0  0 
/dev/sda1                                  /            ext4  errors=remount-ro      0  1 
# /windows was on /dev/sda3 during installation
UUID=D978-3B2C                             /windows     vfat  utf8,umask=007,gid=46  0  1 
# swap was on /dev/sda5 during installation
UUID=da8bbd1f-a2bf-4a0b-875e-d383a88f7111  none         swap  sw                     0  0 
**UUID=2AB88F39B88F0315      /media/WDG2TB  ntfs  defaults               0  0 **
UUID=68B04048B0401EC6      /media/SAM2TB  ntfs  defaults               0  0 

```MSI K8N NEO-2 Platinum Motherboard has 2 SATA controllers, both of the 2TB drives are on the same controller (the NForce 3 controller).  I tried the other controller and the issue is the same.

Ideas?  Does Ubuntu have any known issues with these WD Green drives (I couldn't find any in the forums)?

---

### Post by flatline403 on 2011-05-19
More Info:

df -h
```

manuel@Natalie:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              92G  2.5G   85G   3% /
none                 1003M  308K 1003M   1% /dev
none                 1007M  416K 1007M   1% /dev/shm
none                 1007M  308K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sdc1             1.9T  1.2T  652G  66% /media/SAM2TB
/dev/sda3              84G   64K   84G   1% /windows
manuel@Natalie:~$ 

```

sudo fdisk -l
```

manuel@Natalie:~$ sudo fdisk -l
[sudo] password for manuel: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c67e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       13374     9764865    5  Extended
/dev/sda3           13374       24322    87938048    b  W95 FAT32
/dev/sda5           12158       13374     9764864   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
16 heads, 63 sectors/track, 3876021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf787955

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     3876018  1953513040+   7  HPFS/NTFS

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0b01aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001    7  HPFS/NTFS
manuel@Natalie:~$ 

```




```

manuel@Natalie:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid    0  0  
/dev/sda1                                  /            ext4  errors=remount-ro      0  1  
# /windows was on /dev/sda3 during installation
UUID=D978-3B2C                             /windows     vfat  utf8,umask=007,gid=46  0  1  
# swap was on /dev/sda5 during installation
UUID=da8bbd1f-a2bf-4a0b-875e-d383a88f7111  none         swap  sw                     0  0  
UUID=2AB88F39B88F0315      /media/WDG2TB  ntfs  defaults               0  0  
UUID=68B04048B0401EC6      /media/SAM2TB  ntfs  defaults               0  0  
manuel@Natalie:~$ 

```

---

### Post by flatline403 on 2011-06-16
Still having this issue.  Anyone have any ideas?

---

### Post by Morbius1 on 2011-06-16
This is a long shot but have you reformatted the drive recently?

"blkid" keeps a cache so you might want to run it like this to clear the cache and force it to start fresh: 
```
sudo blkid -c /dev/null
```
It's possible that the UUID for that partition in fstab is not accurate:

---

