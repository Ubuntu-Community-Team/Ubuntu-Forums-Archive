---
title: "how can i mount this usb drive"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by sparkster666 on 2007-11-20
I am pretty new to linux but I am here to stay 

I am having trouble with an external usb hard drive it will not automatically mount


with drive in

```
john@john-laptop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68fcd7bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         979     7858176   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             979       13897   103763160    7  HPFS/NTFS
/dev/sda3   *       13898       23891    80276805   83  Linux
/dev/sda4           23892       24321     3453975    5  Extended
/dev/sda5           23892       24321     3453943+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeeb729cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    c  W95 FAT32 (LBA)
john@john-laptop:~$ mount
mount          mount.fuse     mount.ntfs     mount.ntfs-3g  mountpoint     
john@john-laptop:~$ mount
mount          mount.fuse     mount.ntfs     mount.ntfs-3g  mountpoint     
john@john-laptop:~$ mount


```

with drive out

```
john@john-laptop:~$ sudo fdisk -l
[sudo] password for john:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68fcd7bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         979     7858176   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             979       13897   103763160    7  HPFS/NTFS
/dev/sda3   *       13898       23891    80276805   83  Linux
/dev/sda4           23892       24321     3453975    5  Extended
/dev/sda5           23892       24321     3453943+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16
john@john-laptop:~$ 

```

how can i mount this drive or even better make it mount automatically

---

### Post by taurus on 2007-11-20
Plug the drive back in and see if you can mount it by hand from a terminal.

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by sparkster666 on 2007-11-20
thanks for you quick reply

```
john@john-laptop:~$ sudo mkdir /media/sdb1
[sudo] password for john:
john@john-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
john@john-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              76G   23G   50G  31% /
varrun               1010M  128K 1009M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   96K 1010M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0              52M   52M     0 100% /media/cdrom0

```

ok I now can get to it with Nautilus but it does not show up on desctop or show in the computer link

is there a way to make it now auto mount or do i have to run that command everytime??

---

