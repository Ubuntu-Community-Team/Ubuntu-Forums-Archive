---
title: "Unable to open external usb hdd"
date: 2013-07-11
forum: Hardware
---

### Post by _jj on 2013-07-11
Just attempted to use a 1tb Western Digital My Passport external usb hard drive with a pretty much default install of xubuntu 12.04, the drive mounts/ejects fine, but when I attempt to access the directory "My Passport" in Thunar I get the error message

```

Failed to open directory "My Passport".
Error when getting information for file '/media/My Passport/Locale': Input/output error.

```

I think this could be a permissions problem, looking at the permissions

```

joe@*****:/media$ ls -l
total 56
drwxrwxrwx 1 root root 12288 Jul  9 15:38 Backup
drwx------ 1 joe  joe   4096 Sep  3  2011 My Passport

```

'My Passport' has a different ownership and permissions than for example my Backup partition (whose permissions are also I think a bit odd as I am using an ntfs formatted partition and had to fiddle things to get it to work) however I don't seem to be able to change My Passports permissions, or I am trying the wrong chmod commands?

Some other perhaps helpful info
```

ls -al /media/My\ Passport/
ls: cannot access /media/My Passport/Locale: Input/output error
ls: cannot access /media/My Passport/My Passport Apps for Mac: Input/output error
ls: cannot access /media/My Passport/User Manuals: Input/output error
total 12
drwx------ 1 joe  joe  4096 Sep  3  2011 .
drwxr-xr-x 8 root root 4096 Jul 11 09:30 ..
drwx------ 1 joe  joe  4096 Feb 14 02:01 Extras
d????????? ? ?    ?       ?            ? Locale
d????????? ? ?    ?       ?            ? My Passport Apps for Mac
drwx------ 1 joe  joe     0 Sep  3  2011 System Volume Information
d????????? ? ?    ?       ?            ? User Manuals

```

and

```

joe@*****:/media$ mount
/dev/sdc1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

Any help/pointers much appreciated!

---

### Post by sudodus on 2013-07-11
It seems you can read the directory 'Extras'

What file system is there on the partition 'My Passport'? Could there be a Mac system?

Have you tried to mount it manually with the ***mount*** command?

```
 sudo mount -t auto /dev/sdxy /mnt
```

where x is the drive letter and y is the partition number, that you can probably figure out from the output of

```
 sudo fdisk -lu
```
or
```
 sudo parted -l
```

Please post the output of those commands as well as the output of
```
sudo blkid
```

---

### Post by _jj on 2013-07-11
> **sudodus said:**
> 
Have you tried to mount it manually with the ***mount*** command?


```
sudo mount -t auto /dev/sdc1 /mnt 
```
Worked fine, but was unable to access /mnt as before when it automounted to 'My Pssport'

The outputs of the commands you asked for

```
 sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b920b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   307406847   153600000    7  HPFS/NTFS/exFAT
/dev/sda3       307408894   622995455   157793281    5  Extended
/dev/sda4       622995456  1953523711   665264128    7  HPFS/NTFS/exFAT
/dev/sda5       307408896   317845503     5218304   82  Linux swap / Solaris
/dev/sda6       317847552   622995455   152573952   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bd15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1331202047   665600000    7  HPFS/NTFS/exFAT
/dev/sdb2      1331202048  1953523711   311160832   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023f15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT



```

```
 sudo parted -l
Model: ATA WDC WD1003FBYX-1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   157GB   157GB   primary   ntfs
 3      157GB   319GB   162GB   extended
 5      157GB   163GB   5344MB  logical   linux-swap(v1)
 6      163GB   319GB   156GB   logical   ext4
 4      319GB   1000GB  681GB   primary   ntfs


Model: ATA WDC WD1003FBYX-1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  682GB   682GB  primary  ntfs
 2      682GB   1000GB  319GB  primary  ext3


Model: WD My Passport 0748 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs

```

```
sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="C660F6AF60F6A579" TYPE="ntfs" 
/dev/sda2: UUID="28B4F904B4F8D4F2" TYPE="ntfs" 
/dev/sda4: LABEL="Storage" UUID="33C0487C4A4BD1EB" TYPE="ntfs" 
/dev/sda5: UUID="25afe596-c6a1-4565-a91a-7e4335e3f6fa" TYPE="swap" 
/dev/sda6: UUID="0d5135d7-b50a-4c64-83be-68b73f970e96" TYPE="ext4" 
/dev/sdb1: LABEL="Backup" UUID="05AD7A350B673D19" TYPE="ntfs" 
/dev/sdb2: UUID="cd94faf5-6aa3-4fc4-9623-66285bd971a6" TYPE="ext3" 
/dev/sdc1: LABEL="My Passport" UUID="4E1AEA7B1AEA6007" TYPE="ntfs" 
```

Does any of that help?  It appears to be an ntfs drive (good for me as ultimately it may well be used on Windows, Linux and Mac systems)

---

### Post by sudodus on 2013-07-11
It looks fine to me according to those commands. But in your first post

```
 ls -al /media/My\ Passport/
```

gives an output with a lot of ?s.

Also from your first post, it seems you can read the directory 'Extras'. Is that so, can you cd into it or browse it with the file browser?

I think there is something wrong with the file system (a small damage, that might be possible to repair, when attached to a computer running Windows. (Rule: Use the original system tools to repair a file system, so repair Windows file systems with Windows and linux file systems with linux ...).

---

### Post by _jj on 2013-07-11
I can cd into it but
```

/media/My Passport/Extras$ ls
ls: reading directory .: Input/output error

```
Should it be possible to simply format this drive and start over, there is nothing of importance on it.

---

### Post by sudodus on 2013-07-11
Certainly :-) This would be the simplest way to get i right. If you want it to be formatted to NTFS, do it in Windows. And make a good descriptive label without space in the label name.

---

### Post by jp734 on 2013-07-11
I have a 2tb external drive that will not let me mount if not as root. They said it is something about FUSE. Not familiar what it is. So my workaround is to run gnome disk utility as root. "Sudo palimpsest" on terminal and mount. Can read it after that. Not the best way but since don't use it much, I'm good with it.

---

