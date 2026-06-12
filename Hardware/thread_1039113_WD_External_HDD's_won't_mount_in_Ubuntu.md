---
title: "WD External HDD's won't mount in Ubuntu"
date: 2009-01-14
forum: Hardware
---

### Post by Peleus on 2009-01-14
Hi all, 

Beginner Linux user installing 8.10 for the first time in a while. 

Having a problem with both of my external hard drives. One is a Western Digital 500gb My Book. The second is the same type but 1TB. 

When I plug them in it simply comes up with unable to mount "Data (name of HDD)". Same thing on the TB drive. 

Any idea's?

Massive beginner, so I apologize if I'm leaving out much needed information to help diagnose the problem. 

Thanks.

---

### Post by taurus on 2009-01-14
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by 6py7 on 2009-01-14
I am having a similar issue.  I am a longtime Windows user who just installed Ubuntu yesterday.  All of my backup files are on my external HD and I just need to be able to access them.  I didn't realize that the HD was in NTFS, so that may be part of it?

Here is what I get in the terminal:
sudo fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92889288

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19081   153268101   83  Linux
/dev/sda2           19082       19457     3020220    5  Extended
/dev/sda5           19082       19457     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

```
and df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   34G  103G  25% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  208K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  501M   1% /dev
tmpfs                 504M  192K  504M   1% /dev/shm
lrm                   504M  2.0M  502M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/scd0             582M  582M     0 100% /media/cdrom0

```

Ubuntu is recognizing the drive in the Places menu, but when I go to mount it it simply won't?  What should I be doing different?

---

### Post by taurus on 2009-01-14
> **6py7 said:**
> I am having a similar issue.  I am a longtime Windows user who just installed Ubuntu yesterday.  All of my backup files are on my external HD and I just need to be able to access them.  I didn't realize that the HD was in NTFS, so that may be part of it?

Here is what I get in the terminal:
sudo fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92889288

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19081   153268101   83  Linux
/dev/sda2           19082       19457     3020220    5  Extended
/dev/sda5           19082       19457     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

```
and df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   34G  103G  25% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  208K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  501M   1% /dev
tmpfs                 504M  192K  504M   1% /dev/shm
lrm                   504M  2.0M  502M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/scd0             582M  582M     0 100% /media/cdrom0

```

Ubuntu is recognizing the drive in the Places menu, but when I go to mount it it simply won't?  What should I be doing different?

See if you can mount it from a terminal with

```
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```

---

### Post by 6py7 on 2009-01-14
Thank you for your help, it works!

---

