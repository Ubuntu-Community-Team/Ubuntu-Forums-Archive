---
title: "mount external hard drive"
date: 2013-04-04
forum: Hardware
---

### Post by parkygis on 2013-04-04
Hello,
I am trying to back up some data from a hard drive(linux format).   After I connect it with usb, it does not show any thing on "home folder".
 Here is a result for "sudo fdisk -l"

Does anyone know how to mound an external hard drive and how to back up files from the drive?

[ATTACH=CONFIG]240931[/ATTACH]

---

### Post by agillator on 2013-04-04
Which drive are you talking about, /dev/sda or /dev/sdb? sdb has no linux partitions so I assume you are talking about sda. From what you have posted you cannot tell whether sda is mounted or not. I assume it is. What directory are you looking for? fdisk doesn't show directories (folders), only partitions. If you are looking for a user's home directory it should be /home/<username>/. When you try to get a directory of that, or just of /home/, what do you get?

---

### Post by coldraven on 2013-04-04
It should mount automatically. When I plug in my external 1TB USB drive it appears in the file manager (Nautilus) in the left hand pane. All external media is mounted at /media/your-user-name/

---

### Post by parkygis on 2013-04-04
I like to connect "/dev/sdb".  I am not sure how to connect to it.  actually, the hard drive is from security camera dvr machine.

---

### Post by parkygis on 2013-04-04
I like to connect "/dev/sdb".  I am not sure how to connect to it.   actually, the hard drive is from security camera dvr machine.

---

### Post by agillator on 2013-04-04
OK. Now it begins to make a little sense. It may or may not automatically mount when connected, that depends on how your system is set up. However, sdb as shown in your original message is not a 'linux' disk. If you look fdisk identlifies it as Win95 FAT32. 
Check the /media and /mnt directories, see if it is mounted there. If not, use the mount command to mount if manually. To do that, choose (or create) a directory where you wish to mount it. Assume you will mount it at /media/external/. After this directory exists, use the command 'sudo mount -t vfat /dev/sdb1 /media/external'. See what that gives you. Assuming it works and that sdb1 is actually a vfat partition, then you can get a directory and see what is really on there. Since it is from a security camera there is no telling what the actual directory structure is. It may well not be what you expect.

---

### Post by Cheesemill on 2013-04-04
You have more than one partition on your sdb drive, there is a FAT32 partition and a linux partition. There may be more as well as I can't see the rest of your fdisk output in your screenshot.

Can you run the following command and post back the full output please, it's easiest to just copy the result from your terminal and paste it in your reply in between [NOPARSE]```
 
```[/NOPARSE] tags to make it easier for us to read.

```
sudo parted -l
```
(that's a lower case L not a one).

---

### Post by parkygis on 2013-04-04
> **agillator said:**
> OK. Now it begins to make a little sense. It may or may not automatically mount when connected, that depends on how your system is set up. However, sdb as shown in your original message is not a 'linux' disk. If you look fdisk identlifies it as Win95 FAT32. 
Check the /media and /mnt directories, see if it is mounted there. If not, use the mount command to mount if manually. To do that, choose (or create) a directory where you wish to mount it. Assume you will mount it at /media/external/. After this directory exists, use the command 'sudo mount -t vfat /dev/sdb1 /media/external'. See what that gives you. Assuming it works and that sdb1 is actually a vfat partition, then you can get a directory and see what is really on there. Since it is from a security camera there is no telling what the actual directory structure is. It may well not be what you expect.

thanks for the quick response.
I am getting a result as follows.
```
james@james-Compaq-Mini-110c-1100:~$ sudo mount -t vfat /dev/sdb1 /media
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by parkygis on 2013-04-04
> **Cheesemill said:**
> You have more than one partition on your sdb drive, there is a FAT32 partition and a linux partition. There may be more as well as I can't see the rest of your fdisk output in your screenshot.

Can you run the following command and post back the full output please, it's easiest to just copy the result from your terminal and paste it in your reply in between [NOPARSE]```
 
```[/NOPARSE] tags to make it easier for us to read.

```
sudo parted -l
```
(that's a lower case L not a one).

I am getting a result as follows.
```
james@james-Compaq-Mini-110c-1100:~$ sudo parted -l
Model: ATA SAMSUNG HM160HI (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  159GB  159GB   primary   ext4            boot
 2      159GB   160GB  1063MB  extended
 5      159GB   160GB  1063MB  logical   linux-swap(v1)


Error: Can't have a partition outside the disk! 

```

---

### Post by Cheesemill on 2013-04-04
There's something funny going on with the partitions on the external drive, as parted isn't showing it at all.
Can you post the results of...
```
sudo fdisk -l /dev/sdb
```

---

### Post by agillator on 2013-04-04
GParted should give you more information than fdisk does. Try 'gksu gparted'. In the upper right of the window is a box that should show /dev/sda. Click the arrow and select /dev/sdb. See what it says about that, especially what type of filesystem it shows for each partition. Select a partition and then open the the partition menu at the top of the window. See if there is a mount option there. If so, click it and see what happens. If there is an unmount option instead of mount, then the partition is already mounted.

I am suspecting that, since this came from a security camera system, it has been set up with a weird partition table. We may or may not be able to do anything, but we'll try. There are still a few tricks available. It also sounds as if cheesemill has more experience in this area than I, so we'll see what cheesemill has to suggest.

---

### Post by parkygis on 2013-04-05
> **Cheesemill said:**
> There's something funny going on with the partitions on the external drive, as parted isn't showing it at all.
Can you post the results of...
```
sudo fdisk -l /dev/sdb
```

hello, this is the result.

```
james@james-Compaq-Mini-110c-1100:~$ sudo fdisk -l /dev/sdb
[sudo] password for james: 
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    16016804    64066968    c  W95 FAT32 (LBA)
/dev/sdb2        16016805  1953520064  3455045744   83  Linux


```

---

### Post by parkygis on 2013-04-05
> **Cheesemill said:**
> There's something funny going on with the partitions on the external drive, as parted isn't showing it at all.
Can you post the results of...
```
sudo fdisk -l /dev/sdb
```


here is the result.
```
james@james-Compaq-Mini-110c-1100:~$ sudo fdisk -l /dev/sdb
[sudo] password for james: 
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    16016804    64066968    c  W95 FAT32 (LBA)
/dev/sdb2        16016805  1953520064  3455045744   83  Linux


```

---

### Post by parkygis on 2013-04-05
here is the result.
```
james@james-Compaq-Mini-110c-1100:~$ sudo fdisk -l /dev/sdb
[sudo] password for james: 
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    16016804    64066968    c  W95 FAT32 (LBA)
/dev/sdb2        16016805  1953520064  3455045744   83  Linux


```

---

### Post by parkygis on 2013-04-05
> **Cheesemill said:**
> There's something funny going on with the partitions on the external drive, as parted isn't showing it at all.
Can you post the results of...
```
sudo fdisk -l /dev/sdb
```

Here is the results.
```


james@james-Compaq-Mini-110c-1100:~$ sudo fdisk -l /dev/sdb
[sudo] password for james: 
Note: sector size is 4096 (not 512)
 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    16016804    64066968    c  W95 FAT32 (LBA)
/dev/sdb2        16016805  1953520064  3455045744   83  Linux

```

---

### Post by parkygis on 2013-04-05
```

james@james-Compaq-Mini-110c-1100:~$ sudo fdisk -l /dev/sdb
[sudo] password for james: 
Note: sector size is 4096 (not 512)
 
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    16016804    64066968    c  W95 FAT32 (LBA)
/dev/sdb2        16016805  1953520064  3455045744   83  Linux
```

---

