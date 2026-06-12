---
title: "Can't mount NTSF disk"
date: 2010-10-24
forum: Hardware
---

### Post by arroba3 on 2010-10-24
Hello!

Well, everything worked fine in my Ubuntu 10.10, until I restarted the PC and I got this message from a hard disk I've been using before with ubuntu:
```
Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```
Any ideas?Please help!:(

Thank you!

---

### Post by MedianMajik on 2010-10-24
Googling...
Do you have ntfs-3g installed on 10.10?  Have you tried unmounting the drive in Nautilus?  Try opening a terminal and running ```
man fuser
``` to learn how to force your system to unmount the drive if you are stuck.
  Hard to give any specific tips when your question isn't very detailed.  Break down how it was working fine before and what happened.  Did you commit any major system changes before the restart?

---

### Post by sikander3786 on 2010-10-24
Please post the output of,

```
sudo fdisk -l
```

```
sudo blkid
```

```
cat /etc/fstab
```

---

### Post by oldfred on 2010-10-24
Did you hibernate your windows install, or does the NTFS partition need chkdsk run? Gparted & Ubuntu do not want to open NTFS partitions with flags set where writing data then may prevent repairs from windows.

---

### Post by nikhilbuwa on 2010-10-24
i have the same problem.i have installed the ubuntu 10.10 on USB drive. earlier i could access all the drives from the HDD but not i get this msg. actually i think my HDD is off since there is no vibrations on my laptop body & nor does the HDD light(led) glows. This means ubuntu only used USB drive. memory cards are detected & other USB's also, but they are FAT32, so i dont understand whats the prob.:confused: & i am new 2 ubuntu so plz help me out. & yeah HDD works fine in windows.
also tried:-
> ubuntu@ubuntu:~$ fuser -m /dev/sda3
Cannot stat file /proc/14096/fd/21: Stale NFS file handle
ubuntu@ubuntu:~$ fuser -m /dev/sda3
Cannot stat file /proc/14096/fd/21: Stale NFS file handle
ubuntu@ubuntu:~$ fuser -km /dev/sda3
Cannot stat file /proc/14096/fd/21: Stale NFS file handle
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x145380eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10147    81499975    7  HPFS/NTFS
/dev/sda2           10147       16915    54362112    7  HPFS/NTFS
/dev/sda3           16915       18189    10240000    f  W95 Ext'd (LBA)
/dev/sda4           18190       19457    10185210    7  HPFS/NTFS
/dev/sda5           16915       18189    10238976    7  HPFS/NTFS

Disk /dev/sdb: 2006 MB, 2006974464 bytes
13 heads, 13 sectors/track, 23194 cylinders
Units = cylinders of 169 * 512 = 86528 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23195     1959920    b  W95 FAT32
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="8fe4cf72-d47e-9443-9d61-c23f56690117" TYPE="ext2" 
/dev/sda1: UUID="4A4A6BAC4A6B938B" TYPE="ntfs" 
/dev/sda2: LABEL="New Volume" UUID="7C0088E50088A82A" TYPE="ntfs" 
/dev/sda4: LABEL="PRESARIO_RP" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sda5: LABEL="New Volume" UUID="B83692E53692A442" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="5AD2-CA96" TYPE="vfat" 
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0thanx.

---

### Post by kkivi on 2011-02-02
I experience the same problem.
I boot from 10.10 live pen drive and try to mount 
external usb to restore my Windows . Some time ago I did it
successfuly. Now I cannot mount the drive and even have the same fuser output. The drive itself is OK - automounted on another box with 10.10 (normal install) wihout problems.

---

### Post by eddiekoski on 2011-05-29
I also have this same or similar problem 

[http://ubuntuforums.org/showthread.php?t=1767704&page=2](http://ubuntuforums.org/showthread.php?t=1767704&page=2)

---

### Post by 337379 on 2013-04-21
Have you all solved the problem?

I have found 1 possible solution.

---

### Post by matt_symes on 2013-04-21
They've either found the solution or given up by now.

This thread is over a year old. Let this thread sleep.

**Thread closed.**

---

