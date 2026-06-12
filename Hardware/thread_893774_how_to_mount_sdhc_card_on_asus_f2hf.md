---
title: "how to mount sdhc card on asus f2hf"
date: 2008-08-18
forum: Hardware
---

### Post by eidam655 on 2008-08-18
hello,

i have a 4GB SDHC card, and when i insert it into the card reader, i get no notification of even something was inserted.

however, when reading dmesg, i get this set of messages: [http://pastebin.sk/sk/7831/](http://pastebin.sk/sk/7831/)

after doing
```
mount /dev/sdb/ /media/sdb/
```

i get an error which says
mount: No medium found


is there any way to get it working?

thank you for answers

---

### Post by coffeecat on 2008-08-18
> **eidam655 said:**
> after doing
```
mount /dev/sdb/ /media/sdb/
```i get an error which says
mount: No medium found

With that code you're trying to mount the whole drive, which won't work. You have to mount a specific partition. As it's an SD card I guess it would have a single partition formatted fat32, so you would need to do something like:

```
mount -t vfat /dev/sdb1 /media/sdb1
```Obviously, adjust /media/sdb1 to whatever mountpoint you have created.

However, I have a feeling this may not work. Is that Asus machine a laptop? I'm not familiar with the model number. There seem to be a lot of threads about internal SD card readers not working on various laptops. If the SD card reader is going to work in Ubuntu, it should work with an SD card if it has a FAT32 partition. So, if the above code doesn't work, insert the card and see what output you get from:

```
sudo fdisk -l
```

(That's lower-case L, not one.)

---

### Post by tfosorcim on 2008-08-18
It does not appear to support the SDHC cards; only MMC/ SD/ Mini-SD/ Memory Stick/ MS Pro/ MS-Duo/ MS-Pro-Duo.

[http://www.asus.com/products.aspx?l1=5&l2=24&l3=317&model=1287&modelmenu=2](http://www.asus.com/products.aspx?l1=5&l2=24&l3=317&model=1287&modelmenu=2)

SD cards over 2GB are SDHC I have this problem with my camera 4G card so I got a external card reader.

---

### Post by eidam655 on 2008-08-19
```
eidam@eidam-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69f807c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        5941    45769185    7  HPFS/NTFS
/dev/sda3            5942        9729    30427110    f  W95 Ext'd (LBA)
/dev/sda5            5942        9589    29302528+  83  Linux
/dev/sda6            9590        9729     1124518+  82  Linux swap / Solaris

```

this is what i get from sudo fdisk -l.

tfosorcim: so that means that even a firmware upgrade will not help?

---

### Post by eidam655 on 2008-08-19
```
eidam@eidam-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69f807c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        5941    45769185    7  HPFS/NTFS
/dev/sda3            5942        9729    30427110    f  W95 Ext'd (LBA)
/dev/sda5            5942        9589    29302528+  83  Linux
/dev/sda6            9590        9729     1124518+  82  Linux swap / Solaris

```

this is what i get from sudo fdisk -l.

tfosorcim: so that means that even a firmware upgrade will not help?

---

