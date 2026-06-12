---
title: "How do I add a 3rd hard drive"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by lonegranger on 2006-04-26
Hi all,
         As a new user I need a "cat,sat,mat" explanation on how to get  Linux/Ubuntu to recognise I have a hard drive installed taken fron my XP box which has all my music and vids on it.

Thanks in advance

---

### Post by savas on 2006-04-26
Hi. Can you give information about your partition table. you can post output of 
sudo fdisk -l

---

### Post by Ensnared on 2006-04-26
Alright then :)

First of all, you need to figure out what the hard-drive is named. This goes hand-in-hand with the primary/secondary and master/slave on the IDE-controller (provided you've got IDE drives).

Primary master is /dev/hda
Primary slave is /dev/hdb
Secondary master is /dev/hdc
Secondary slave is /dev/hdd

Each partition on your drive are numbered deviced with the same name, so the first primary partition on your primary master drive will be /dev/hda1, the second primary parition on your primary slave will be /dev/hdb2, etc.
The numbers aren't always chronological - there's a difference between primary and logical paritions. Basically, an IDE drive can only have 4 primary paritions total, including an extended partition split into logical drives.

So - primary partitions are always numbered 1-4, logical drives (within extended partitions) are always numbered 5 of higher.

So for a typical Windows drive with a C, D, and E for instance, chances are it will have one primary partition (C in Windows), and one extended partition, which is split into two logical drives (D and E in Windows). In such a case, linux would number the devices as such:
Windows C would be /dev/hda1
Windows D would be /dev/hda5
Windows E would be /dev/hda6
In addition you'd have a /dev/hda2, which is the extended parition, but since this one is only a placeholder for the logical drives, you can't access it directly (nor would you ever need to).

So with that in mind, you may be able to figure out which hd-device your new drive is, as well as which parition it is. Let's say your drive has one big primary partition only, and it's connected to your primary slave channel - that would make it /dev/hdb1. If so, you can mount it in - say - /mnt/music, like so:
```
sudo mkdir /mnt/music
sudo mount -t vfat /dev/hdb1 /mnt/music -o iocharset=utf8,umask=000
```

This is an example - you can use different mount-options, but this will make it accessible (read _and_ write) to everyone. Also, vfat means FAT or FAT32. If you have NTFS, you'll put ntfs instead - just bare in mind you can't create or delete files or directories on an NTFS-drive in Linux, but you can read to it and modify existing files. However, the default Ubuntu kernel allow _only_ reading of files on an NTFS parition - not modifying.

To make this magic happen when you boot, edit your /etc/fstab-file and put in the following:```
/dev/hdb2     /mnt/music    vfat    iocharset=utf8,umask=000    0   0
```

Hope that helps :)

EDIT
...or use the command savas provided to just see how it's set up instead :p But hey, hopefully my roundabout explanation was atleast a bit educational ;)

---

### Post by lonegranger on 2006-04-26
Hi,
     The output of sudo fdisk -l is as follows :-

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          96       48163+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2          150901      155060     2096609    f  W95 Ext'd (LBA)
/dev/hda3              96      150897    76003515   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5          150901      155060     2096608+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14814   118993423+   7  HPFS/NTFS
/dev/hdb2           14815       14945     1052257+   f  W95 Ext'd (LBA)
/dev/hdb5           14815       14945     1052226    7  HPFS/NTFS

---

### Post by Ensnared on 2006-04-26
Ok, then your Windows drives are hdb1 and hdb5 (hdb2 is the extended partition containing hdb5, and as such isn't actually used as a partition itself), and they're apparently both NTFS.

So first, you need to create the directories where they wil be mounted. I use subdirectories in /mnt/ for this, but that's a matter of preference (and old habit from my earlier Red Hat days). In that case, you first create the directories, and then mount the drives:
```
sudo mkdir /mnt (unless it already exists)
sudo mkdir /mnt/windows_c
sudo mkdir /mnt/windows_d
```Substitute windows_c and windows_d with anything you want to use instead.

Then, mount the drives:```
sudo mount -t ntfs /dev/hdb1 /mnt/windows_c -o iocharset=utf8,umask=000
sudo mount -t ntfs /dev/hdb5 /mnt/windows_d -o iocharset=utf8,umask=000
```

Remember, they will be read-only as the default Ubuntu kernel does not have write-support for NTFS, and even if it did, you would not be able to create or delete files or directories, only modify existing ones.

To mount them automagically on boot, add the following lines to your /etc/fstab:```
/dev/hdb1        /mnt/windows_c   ntfs iocharset=utf8,umask=000     0       0
/dev/hdb5        /mnt/windows_d   ntfs iocharset=utf8,umask=000     0       0
```

Since they will be read-only no matter what, "umask=000" is actually redundant since all that does is allow any user full access to the drives and their content. If you leave it out, everyone will still be able to access it for reading since the default umask is 022 (e.g. rwxr-xr-x - read/write/execute for the owner, which is root, and read/execute for everyone else).

The "iocharset=utf8" is important to make sure the filenames and directories are interpreted as being encoded with the UTF-8 charset, which is the one Windows uses. Without it, you risk getting some characters not showing up right on those drives when they're mounted.

---

