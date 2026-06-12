---
title: "recovering disappeared (not deleted) files"
date: 2013-05-11
forum: Hardware
---

### Post by scarab on 2013-05-11
Just did a backup of about 118 Gb to an external drive w several other things in it. The folder to which I copied the backup files is shown as empty (mounted again and same), trash and hidden folders are empty or with other things, but the amount of space of the files backed up (118 Gb) is shown as used disk space (mean, the disk usage increased by 118 Gb after the backup and continues to be so). How can I recover those files? I am completely sure they are there, they are probably still named, they have not been trashed, but they do not appear in dolphin not even as hidden.... any ideas will be welcome, I only found tutorials on how to recover deleted files or partitions, not files that appear not to have been deleted and that are not shown as free space.

---

### Post by Bashing-om on 2013-05-11
scarab; Hi !

I would think that if one were to manually mount that backup partition:
A way can be found to list all contents :
```
 sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup ## assumes  the backup partition is 1st partition 2nd drive
ls -la /mnt/backup ##assumes you have authority to access the backup partition as the current user
#else try// sudo ls -la /mnt/backup
#else2 consider ownership issues// sudo chown <USERNAME>:<USERNAME> /mnt/backup/<some_directory_name>
##then may also consider if lots of directories in /backup are not owned by you, recursively changing ownership to them.
```

Do not forget to unmount that drive when done and prior to logging off !!

REMEMBER to unmount:
```
sudo umount /mnt/backup
```[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by scarab on 2013-05-12
Hi and thanks for reply!

did it and something more and got:

vaz-de-mello@vaz-de-mello-Vostro1510:~$ ls -la /mnt/backup
total 3132
drwxrwxrwx 1 root root    8192 May 11 19:10 .
drwxr-xr-x 3 root root    4096 May 12 09:04 ..
drwxrwxrwx 1 root root       0 May 11 19:10 backfer
drwxrwxrwx 1 root root   61440 May 11 15:07 backupfer11-v-2013
drwxrwxrwx 1 root root    4096 May 11 19:02 backups
drwxrwxrwx 1 root root    4096 May 10 20:59 BACKUPSil10-v-2013
drwxrwxrwx 1 root root    4096 Feb 16 18:40 dichotomius
-rwxrwxrwx 1 root root  812544 Jul  7  2007 DoubleKiller.exe
drwxrwxrwx 1 root root   12288 Jan 28 06:25 Espécies avaliadas IUCN
drwxrwxrwx 1 root root       0 May 11 09:37 ludico
drwxrwxrwx 1 root root  958464 May 11 12:31 PDF
drwxrwxrwx 1 root root   20480 Feb 16 18:40 Pictures
-rwxrwxrwx 2 root root 1302771 Feb  3  2010 Quick Reference Guide.pdf
drwxrwxrwx 1 root root    4096 May 11 12:55 .Trash-1000
drwxrwxrwx 1 root root    4096 May 11 08:16 .Trash-1001
vaz-de-mello@vaz-de-mello-Vostro1510:~$ cd /mnt/backup
vaz-de-mello@vaz-de-mello-Vostro1510:/mnt/backup$ ls
backfer             backups             dichotomius       Espécies avaliadas IUCN  PDF       Quick Reference Guide.pdf
backupfer11-v-2013  BACKUPSil10-v-2013  DoubleKiller.exe  ludico                   Pictures
vaz-de-mello@vaz-de-mello-Vostro1510:/mnt/backup$ cd backupfer11-v-2013/
vaz-de-mello@vaz-de-mello-Vostro1510:/mnt/backup/backupfer11-v-2013$ ls
ls: reading directory .: Input/output error

this last backupfer11-v-2013 is the folder to which I copied my data. is that final error sign of no data or of the possibility of having data in it? and then how to recover it?

it is not really a backup partition in an external drive, I only backed up data to an external drive without making any new partition, to a simple folder in it. the folder appears as empty, but the amount of space needed for my files (that took about two hours to be copied and I have no other copy now) is counted as used space in that external hd. I mean, the amount of used storage in the hd increased by 118 Gb, but those 118 Gb are not available, nor have been deleted, they have been copied but apparently not "indexed" or something like that. I have no knowledge about all that anyway.

any further ideas?

---

### Post by Bashing-om on 2013-05-12
scarab;

Off the top of my head I would consider the possibility that the data within "backupfer11-v-2013" is corrupted...so that error indicates to me.

Before running a file system check/repair..let's look and see what we are dealing with.
Terminal codes:
```
sudo fdisk -lu #to see the partitions' sizes and layout
du -h --max-depth=1 | sort -hr #to see the disk usage from files point of view
```

Nope this is too soon of a procedure... the "backupfer11-v-2013" directory is owned by "root" and a normal user does not have access to it.
What results from listing that directory using elevated privileges ?
```
sudo ls -la /mnt/backup/backupfer11-v-2013
```

Putting the file system checks on-hold . [INDENT=2]
try'n to see what is to be seen

[/INDENT]

---

### Post by scarab on 2013-05-12
thanks again and in advance!

here results:

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c3d77d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1465147119   732572536    7  HPFS/NTFS/exFAT

vazdemello@vazdemello-Vostro1510:/mnt/backup/backupfer11-v-2013$ du -h --max-depth=1 | sort -hr
60K     

meaning probably no file is there?

and then

vazdemello@vazdemello-Vostro1510:/mnt/backup/backupfer11-v-2013$ sudo ls -la /mnt/backup/backupfer11-v-2013
ls: reading directory /mnt/backup/backupfer11-v-2013: Input/output error
total 0

hmpf.....

---

### Post by Bashing-om on 2013-05-12
scarab;

Not sure at all, data is on that drive sdb, fdisk says the blocks are allocated;
fdisk shows the partitioning to be Windows' NTFS, perhaps linux disk utility (du) can not read the NTFS scheme ??

What I suggest at this point is to take that disk to a Windows machine, see if Windows sees it, and as it is NTFS use Windows's file utilities to repair that file system. Then see again about mounting that partition in ubuntu.
[INDENT=2]
just my thoughts on the matter

[/INDENT]

---

