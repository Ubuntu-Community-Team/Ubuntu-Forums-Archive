---
title: "my fstab is gone, cant get into gui now"
date: 2008-10-26
forum: General Help
---

### Post by king james on 2008-10-26
I deleted via "rm" /etc/fstab /etc/fstab.bak and /etc/fstab~. I thought a new file would automatically be generated, which of course did not happen and now I can't even get to the gui. 

I am going to try pysdm from the command line, can I do anything else?

---

### Post by drs305 on 2008-10-26
Are you in your OS at present? 

If so, don't reboot. Run the following and we may be able to restore some semblance of it for you:
```

mount
sudo fdisk -l
sudo blkid

```

---

### Post by orlox on 2008-10-26
You could also use a live cd to restore your fstab

---

### Post by king james on 2008-10-27
Too late drs305, I booted into windows as my gui was inaccessible. I am in Linux again, and I am going to ask for help this time to get everything mounted properly. 

I did as orlox suggested, and booted into live cd then I copied that to my current /etc/fstab. Here is what it looks like at the moment:

[B]unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0[/B]

Now, it will pick up my windows ntfs partition, but not automatically. My other ide hard drive "my book" is not able to be mounted, but in the live cd it was. 

I already have directories set up in my /media folder called "windows" and "mybook." 

I just checked my windows partition, which was mounted, and changed the mount point from /media/disk to /media/windows. Upon doing so, I can no longer mount it. 

Suggestions? 

BTW, my "my book" is a fat32 and windows is ntfs.

---

### Post by rsambuca on 2008-10-27
Post the output of the fdisk -l and blkid commands.

---

### Post by king james on 2008-10-27
fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b275b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       24906    97659135   83  Linux
/dev/sdb3           24907       24967      489982+  82  Linux swap / Solaris


blkid:
/dev/sda1: LABEL="My Book" UUID="B818-BBA2" TYPE="vfat" 
/dev/sdb1: UUID="B294DF7294DF3795" TYPE="ntfs" 
/dev/sdb2: UUID="aca2babb-cec8-44f3-9d61-6c1236789471" TYPE="ext3" 
/dev/sdb3: TYPE="swap" UUID="86b8496b-01ad-4ac8-85b8-368d2c8e70a3"

---

### Post by rsambuca on 2008-10-27
> **king james said:**
> fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b275b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       24906    97659135   83  Linux
/dev/sdb3           24907       24967      489982+  82  Linux swap / Solaris


blkid:
/dev/sda1: LABEL="My Book" UUID="B818-BBA2" TYPE="vfat" 
/dev/sdb1: UUID="B294DF7294DF3795" TYPE="ntfs" 
/dev/sdb2: UUID="aca2babb-cec8-44f3-9d61-6c1236789471" TYPE="ext3" 
/dev/sdb3: TYPE="swap" UUID="86b8496b-01ad-4ac8-85b8-368d2c8e70a3"
OK, I think you might want something like this for your fstab:```
proc /proc proc defaults 0 0
UUID=aca2babb-cec8-44f3-9d61-6c1236789471 / ext3 relatime,errors=remount-ro 0 1
UUID=86b8496b-01ad-4ac8-85b8-368d2c8e70a3 swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```You can also add your windows partitions too if you prefer.

---

