---
title: "Formatiing an External Hardisk to FAT32"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by ramnarayan on 2005-12-24
Hi

I just purchased an external usbdisk harddisk (80 gb- laptop model). Currently it is formatted as NTFS. However I want to use it as a backup to for my Ubuntu Linux Laptop. 

One major headache is that I need to carry this around and be able to use it on other wincing OS's so had the following queries:
1. Would FAT32 be a good option - being accessible from both Linux OS's and wincedows as well
2. Is there a limit on the size of FAT32 partitions
3. Will rsync work from a EXT3 file system to a FAT32 system and will there be any data problems - if so what

Is this the command i should use
# cfdisk /media/usbdisk

will appreciate the advice and suggestions.

thanks
ram

---

### Post by dabeej on 2005-12-24
[QUOTE=ramnarayan]Hi

I just purchased an external usbdisk harddisk (80 gb- laptop model). Currently it is formatted as NTFS. However I want to use it as a backup to for my Ubuntu Linux Laptop. 

One major headache is that I need to carry this around and be able to use it on other wincing OS's so had the following queries:
1. Would FAT32 be a good option - being accessible from both Linux OS's and wincedows as well
2. Is there a limit on the size of FAT32 partitions
3. Will rsync work from a EXT3 file system to a FAT32 system and will there be any data problems - if so what

Is this the command i should use
# cfdisk /media/usbdisk

will appreciate the advice and suggestions.

thanks
ram[/QUOTE]


Yes, unfortunately fat32 is the only way to go. No file permissions. So I don't know about rsync. There is a 3gb file size limit for Fat32.

oh and the command to create a fat32 fs is

```

sudo /sbin/mkfs.vfat -F 32
```

man mkfs.vfat for more info

---

### Post by ramnarayan on 2005-12-24
Thanks,

again a query or too

[QUOTE=dabeej]Yes, unfortunately fat32 is the only way to go. No file permissions. So I don't know about rsync. There is a 3gb file size limit for Fat32.

Is there a limit on the partition size itself (that is can I make the entire 80 GB FAT32)

thanks
ram

---

### Post by Delkster on 2005-12-24
[QUOTE=ramnarayan]Is there a limit on the partition size itself (that is can I make the entire 80 GB FAT32)[/QUOTE]
The theoretical limit to the size of a FAT partition is 2 terabytes so you aren't likely to run into that for a while. However, I don't know if there are other limitations in the VFAT support of Linux or the filesystem management tools like mkfs. Windows 2000 and XP won't create FAT filesystems larger than 32 GiB but they will readily mount and read such large partitions if they've been created elsewhere.

---

### Post by afhp on 2005-12-24
[QUOTE=ramnarayan]
3. Will rsync work from a EXT3 file system to a FAT32 system and will there be any data problems - if so what
[/QUOTE]

rsync shouldn't care about the underlying filesystems, as long as the filenames can be maintained across. The only problem you'll have is with the file permissions that FAT32 doesn't support -- so if it's purely for backup purposes, you'll be better off archiving your files locally (with zip or tar or any other such program that will keep track of file permissions) and transfer the archive file to the FAT disk. 

> Is this the command i should use
# cfdisk /media/usbdisk


That allows you to (re)partition the disk. In order to format it, you'll need the mkfs command as dabeej said.

---

