---
title: "reformatting old hd, error"
date: 2010-04-15
forum: Hardware
---

### Post by SnickerSnack on 2010-04-15
Hi all,

I went through an old hd to make sure I didn't need anything on it, and after verifying that I don't, I deleted the two partitions on it using the "disk utility".  Well, I wanted to make it into one big partition for extra storage, but the "disk utility" didn't have FAT32 as a file system option, so I decided to use fdisk.

Well, I thought I did it correctly, create new partition, change partition label, then write changes and exit, but there was a problem:

```
zsharon@Weierstrass:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb6cc0bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         833     6297448+  27  Unknown
/dev/sda2   *         834       13159    93184000    7  HPFS/NTFS
/dev/sda3           13160       41346   213086129    5  Extended
/dev/sda5           13160       15239    15719571   83  Linux
/dev/sda6           15239       17318    15719571   83  Linux
/dev/sda7           17318       19397    15719571   83  Linux
/dev/sda8           19398       19953     4200966   82  Linux swap / Solaris
/dev/sda9           19953       24287    32764536   83  Linux
/dev/sda10          24287       41346   128961756    b  W95 FAT32

Disk /dev/sdb: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    b  W95 FAT32
zsharon@Weierstrass:~$ ls /mnt
isoimage0  mediaShare  usbtemp
zsharon@Weierstrass:~$ mount /dev/sdb1 /mnt/mediaShare/
mount: only root can do that
zsharon@Weierstrass:~$ sudo mount /dev/sdb1 /mnt/mediaShare/
mount: unknown filesystem type 'linux_raid_member'
```

Huh?  I think the drive used to be part of a raid array, so do I need to change the jumpers between the ide and power sockets?  Is there something else I need to do?

And, I guess I have another disk just like this one, since I think it was RAID 1 setup.  It is not currently viable for me to use both at once.

Help?

edit: also, the whole process was very fast for a 120 gig hd, so I'm guessing that I did something wrong.

---

### Post by srs5694 on 2010-04-16
The Linux fdisk program edits the partition table, but not the partitions' contents. Since you want to create a FAT filesystem, you must use either the mkdosfs utility:

```

sudo mkdosfs /dev/sdb1

```

There are various options you can use to set a volume name and otherwise tweak it; type "man mkdosfs" for details.

It's possible that you'll need to install the dosfstools package. It's also possible that GParted didn't give you a FAT option because this package wasn't installed, so after installing it you may be able to use GParted for this, should you decide to do so.

---

### Post by SnickerSnack on 2010-04-16
Thanks.  I installed gparted, and it seems to do what I want.  Apt doesn't seem to have mkdosfs.  "apt-cache search mkdosfs" returns only dosfstools.

edit:  It still has the same problem:

```

zsharon@Weierstrass:~$ sudo mount /dev/sdb1 /mnt/mediaShare/
[sudo] password for zsharon: 
mount: unknown filesystem type 'linux_raid_member'

```

---

### Post by srs5694 on 2010-04-16
Please note what I wrote originally (emphasis added):

[quote=srs5694]It's possible that you'll need to install the **dosfstools** package.[/quote]

---

### Post by SnickerSnack on 2010-04-16
> **srs5694 said:**
> Please note what I wrote originally (emphasis added):

That package is already installed.

I think that the filesystem is being made, but the fact that it was once a raid array seems to be a problem.

edit:

Okay, problem solved.

It turns out that I need not use gparted at all.  I only needed Palimpsest Disk Utility:

1. highlight the harddisk, go edit>erase.
2. create partition table
3. create fat partition (it's actually fat32, but it just doesn't say that until afterward)
4. done

Thanks for your input, srs5694.

---

