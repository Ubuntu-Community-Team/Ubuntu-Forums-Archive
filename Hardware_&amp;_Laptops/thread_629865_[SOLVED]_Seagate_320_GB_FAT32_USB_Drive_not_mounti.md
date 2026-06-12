---
title: "[SOLVED] Seagate 320 GB FAT32 USB Drive not mounting."
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by gcastell on 2007-12-02
Hi everybody,

Here is my problem, I have a seagate 320gb (really 298gb) formatted with FAT32, it works perfectly in WinXP and Vista. When I plugged it in Ubuntu, it didn't automount, so here is what I did:

1. Make sure that I safely remove it from the window machine.
2. Update ntfs-3g and ntfs-install and restart my computer.

Neither work.
Now to give you some debug info:

GParted can see the drive.
I can manually mounted by doing this:
```

sudo mkdir /mnt/seagate
sudo mount -t vfat /dev/sda1 /mnt/seagate

```
 and here is the output of lsusb

```

Bus 004 Device 002: ID 0bc2:0503 Seagate RSS LLC 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:2f11 Hewlett-Packard 
Bus 001 Device 003: ID 04e8:323a Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000  

```

and here is the output of fdisk -l


```

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e639e63

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1476    11855938+   7  HPFS/NTFS
/dev/hda2   *        1477        2385     7301542+  83  Linux
/dev/hda3            2386        2432      377527+   5  Extended
/dev/hda5            2386        2432      377496   82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    c  W95 FAT32 (LBA)

```


any idea?

Thanks

---

### Post by gcastell on 2007-12-03
Ok, I give up and formatted the drive with ext3 and now it mounts!! but it is now read only, any ideas?

---

### Post by gcastell on 2007-12-03
Ok, I solved it but using this command:


```

sudo chown halon:halon -R /media/disk

```

it is a shame and it just didn't work, but at least I made it work.

Gabriel

---

### Post by gameryoshi600 on 2008-05-05
i'm going to try if it will work with my seagate 100 GB.

---

