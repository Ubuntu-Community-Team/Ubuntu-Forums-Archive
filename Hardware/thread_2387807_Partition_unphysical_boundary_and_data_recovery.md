---
title: "Partition unphysical boundary and data recovery"
date: 2018-03-24
forum: Hardware
---

### Post by simoncks1994 on 2018-03-24
Hi everyone,

A few weeks ago I messed up my partition. I have important data stored within and I have already backup-ed them by ```
dd if=/dev/sda of=/dev/sdb
``` in another HDD.

Right not I am booting my Desktop with a USB in "try Ubuntu". Opening Gparted returns this error:
```
[FONT=arial]The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.[/FONT]
```

I believe it is the source of the problem, but I am not confident in how to reset the partition start. This is more a headache when I want to recover the data.

I hope the information below would be helpful.

```
[FONT=arial]root@ubuntu:/home/ubuntu# fdisk -l[/FONT]
[FONT=arial]Disk /dev/loop0: 1.5 GiB, 1564921856 bytes, 3056488 sectors[/FONT]
[FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]




[FONT=arial]Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors[/FONT]
[FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disklabel type: dos[/FONT]
[FONT=arial]Disk identifier: 0xe176b393[/FONT]

[FONT=arial]Device     Boot      Start        End    Sectors  Size Id Type[/FONT]
[FONT=arial]/dev/sda1  *          2048 3840167935 3840165888  1.8T 83 Linux[/FONT]
[FONT=arial]/dev/sda2       3840169982 3907028991   66859010 31.9G  5 Extended[/FONT]
[FONT=arial]/dev/sda5       3840169984 3907028991   66859008 31.9G 82 Linux swap / Solaris[/FONT]

[FONT=arial]Partition 2 does not start on physical sector boundary.[/FONT]


[FONT=arial]Disk /dev/sdb: 7.6 GiB, 8178892800 bytes, 15974400 sectors[/FONT]
[FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disklabel type: dos[/FONT]
[FONT=arial]Disk identifier: 0x550f2a26[/FONT]

[FONT=arial]Device     Boot   Start     End Sectors  Size Id Type[/FONT]
[FONT=arial]/dev/sdb1  *          0 3172287 3172288  1.5G  0 Empty[/FONT]
[FONT=arial]/dev/sdb2       3138412 3143147    4736  2.3M ef EFI (FAT-12/16/32)[/FONT]

```
[IMG]https://ibb.co/bwyYen[/IMG]

I appreciate any suggestion. Thanks in advance. :D

Simon

---

### Post by oldfred on 2018-03-24
Please attach screen shots, not post in line. You can easily attach with Forum's advanced editor and paperclip icon.
Not everyone has high speed Internet or may have bandwidth limits and in line screens shots may cause them issues.

The driver descriptor error is usually from the way the live installer is configured and the error is on it. So you can ignore it.

You show one large Linux partition.
First then to try is fsck.

        To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by simoncks1994 on 2018-03-24
Thank you oldfred.

It works like a charm. The partition was automatically recovered. Though there was kernel problem and I had to boot into recovery mode to update, overall my data were saved.

---

### Post by oldfred on 2018-03-25
Glad that worked.

Best to have good backups. dd is not really a backup.

 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

---

### Post by simoncks1994 on 2018-04-05
[SIZE=2]Thanks[/SIZE][SIZE=2] [/SIZE][SIZE=2]oldfred[/SIZE][SIZE=2]. Sorry for the delay. Finally escaped from my busy week.

I think I will take either [/SIZE][SIZE=1][FONT=arial]Déjà Dup[/FONT][/SIZE][SIZE=2],back in time or Veeam. I might want to backup remotely. In that case, perhaps rsync would work.
[/SIZE]

---

