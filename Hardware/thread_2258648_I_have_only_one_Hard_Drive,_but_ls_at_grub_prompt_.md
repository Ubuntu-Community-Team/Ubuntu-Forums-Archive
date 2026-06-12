---
title: "I have only one Hard Drive, but ls at grub prompt lists many... How?"
date: 2014-12-29
forum: Hardware
---

### Post by black8 on 2014-12-29
Hey,


My laptop has a harddrive and a CD/DVD drive. I have not connected any flashdrives to the laptop during boottime. but whenever i type ls at the grub prompt, i get this result. The question might be silly and the answerd obvious, but why?

[img]http://i.imgur.com/kIEtZEL.jpg[/img]


sorry for the clumsy image, but why is there hd0, hd1, hd2, hd3, etc.?

---

### Post by sudodus on 2014-12-29
I don't know yet. Maybe grub does not understand the information in a partition table properly. If the computer can boot into linux, please post the output of the following commands (and put it within [noparse]```
[/noparse] tags).

[CODE]sudo parted -l
```

... space minus ell

```
sudo blkid
```

```
df
```

---

### Post by black8 on 2014-12-30
```

Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          hidden
 2      274MB   1819MB  1546MB  ntfs            Basic data partition          hidden, diag
 3      1819MB  2092MB  273MB   fat32           EFI system partition          boot, esp
 4      2092MB  2226MB  134MB                   Microsoft reserved partition  msftres
 5      2226MB  110GB   108GB   ntfs            Basic data partition          msftdata
 6      110GB   110GB   472MB   ntfs                                          hidden, diag
 7      110GB   229GB   119GB   ntfs            Basic data partition          msftdata
 8      229GB   279GB   50.0GB  ext4                                          msftdata
13      279GB   346GB   67.0GB  ext4                                          msftdata
14      346GB   349GB   2248MB  ext4                                          msftdata
10      349GB   390GB   41.0GB  ext4
11      390GB   395GB   5120MB  linux-swap(v1)
12      395GB   468GB   73.2GB  ext4
 9      468GB   500GB   32.1GB  ntfs            Basic data partition          hidden, diag

```

```
/dev/sda1: LABEL="SONYSYS" UUID="3817-4F5E" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="229f8582-9b72-423d-85b5-968b6b5dcfa5" 
/dev/sda2: LABEL="Windows RE tools" UUID="6E66A4ED66A4B6ED" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="5123fc57-365d-4fb9-b9bb-32e06846fb61" 
/dev/sda3: UUID="FC4C-5359" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6c97c4a7-74de-489b-9bdc-450aa137d3d8" 
/dev/sda4: PARTLABEL="Microsoft reserved partition" PARTUUID="8d794c32-abe7-40f2-b1e4-c121960b2015" 
/dev/sda5: UUID="7E541B44541AFF19" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="8a8273a1-fabd-458f-96e1-1a787f7d36bd" 
/dev/sda6: UUID="2458A1D558A1A650" TYPE="ntfs" PARTUUID="611483f5-5b5a-4903-beae-601d3807b5eb" 
/dev/sda7: LABEL="Windows Storage" UUID="7CF0E801F0E7BF8E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="ca3b94eb-44ef-42fe-a27b-b7bbe83aa6e2" 
/dev/sda8: UUID="50183e48-8e7d-42b8-b50a-57e7d2faead5" TYPE="ext4" PTTYPE="dos" PARTUUID="60f89f6e-a3ec-46df-b05f-4cee57f8637b" 
/dev/sda9: LABEL="Recovery" UUID="C858AB1558AB0174" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="2dc8f384-7db3-4ee1-b01c-2ba036441d1b" 
/dev/sda10: UUID="7ffea175-1456-488e-8fb1-1b76693b36aa" TYPE="ext4" PARTUUID="07da1bea-1fa9-4a3c-b0dd-a65d33b48245" 
/dev/sda11: UUID="8327984d-b00e-4632-be86-7d0a57d4f1be" TYPE="swap" PARTUUID="4147b48e-2a9d-4581-87e2-0bf20f2f512f" 
/dev/sda12: UUID="2d9483a8-9e31-4f36-89ca-9bbdb5f684e9" TYPE="ext4" PARTUUID="5630992c-73ba-4e90-9006-dfacebb20d24" 
/dev/sda13: UUID="ea2e83f9-b7cb-45b7-bd95-83bf45a7f2d9" TYPE="ext4" PARTUUID="c1f79598-a920-48c4-b18e-c0790119a143" 
/dev/sda14: UUID="eda709f7-b8b0-430f-bbd2-8d3b0eccdb56" TYPE="ext4" PARTUUID="62c10f13-fc6c-43f7-a575-e7b91ff663b0" 

```

```
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda10      39241336  4922156  32302772  14% /
none                   4        0         4   0% /sys/fs/cgroup
udev              917368        4    917364   1% /dev
tmpfs             185700     1076    184624   1% /run
none                5120        4      5116   1% /run/lock
none              928484      300    928184   1% /run/shm
none              102400       40    102360   1% /run/user
/dev/sda12      70201784 13783148  52829468  21% /home
/dev/sda3         258048    47484    210564  19% /boot/efi


```

---

### Post by sudodus on 2014-12-30
It seems these linux commands (parted, blkid, df) can read the drive and show the partition table in a good way, while the primitive grub tool 'ls' cannot do it. I suspect that 'ls' in grub does not handle gpt partition information correctly. As long as grub can boot like it should, you need not worry about this confusion in grub.

---

### Post by oldfred on 2014-12-30
Do you have a USB multicard reader plugged in? My drive count rises a lot when I plug mine in. 

And I did notice with my new install, my sdb drive was seen as sdc. But only other device is a DVD, so UEFI/BIOS/grub must have counted it? Or flash drive was promoted to sdb. May be how UEFI enumerates ports and boot devices.

---

