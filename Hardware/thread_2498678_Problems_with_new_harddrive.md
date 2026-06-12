---
title: "Problems with new harddrive"
date: 2024-06-23
forum: Hardware
---

### Post by claus on 2024-06-23
Hi all,

all-of-a-sudden, I cannot write on my new harddrive. Attempts to set the proper rights in Caja failed. After performing **'sudo chown -cR claus new_drive'**, now I cannot read the drive either. I have no clue what's the matter here. A few days ago, everything was fine.
What can I do to solve this issue?

Claus

---

### Post by #&amp;thj^% on 2024-06-23
Single or Dual Boot, If it is, is Windows one?
Also check in:
```
stat /home/$USER && stat /usr/share/dbus-1
  File: /home/me
  Size: 76        	Blocks: 66         IO Block: 16384  directory
Device: 0,51	Inode: 2           Links: 31
Access: (0750/drwxr-x---)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2024-06-23 11:05:35.464840775 -0600
Modify: 2024-06-23 11:05:35.462840809 -0600
Change: 2024-06-23 11:05:35.462840809 -0600
 Birth: 2024-05-06 10:14:28.418649015 -0600
  File: /usr/share/dbus-1
  Size: 9         	Blocks: 18         IO Block: 1024   directory
Device: 0,27	Inode: 53914       Links: 7
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-06-03 10:55:26.968990547 -0600
Modify: 2024-06-15 15:12:25.287506612 -0600
Change: 2024-06-15 15:12:25.287506612 -0600
 Birth: 2024-05-06 10:05:26.838394168 -0600

```

It wouldn't hurt to see this as well:
```
df -hT
```

---

### Post by yancek on 2024-06-23
Is this an external drive you want to use for data and as asked above, what filesystem type is it?  When you ran the chown command, were you in the directory immediately above new_drive and did that mount point actually exist.  Is this a partition on the drive or just a single directory?

---

### Post by claus on 2024-06-23
File system    Type   Size    Size               % Mounted on
tmpfs          tmpfs  1,6G    2,0M  1,6G    1% /run
/dev/sda2      ext4   219G    204G  3,5G   99% /
tmpfs          tmpfs  7,8G     22M  7,8G    1% /dev/shm
tmpfs          tmpfs  5,0M    4,0K  5,0M    1% /run/lock
/dev/sda1      vfat   511M    6,1M  505M    2% /boot/efi
/dev/sdb1      vfat   299G     46G  253G   16% /home/claus/neue_Platte -> this ist the harddrive
tmpfs          tmpfs  1,6G    172K  1,6G    1% /run/user/1000

---

### Post by claus on 2024-06-23
> **yancek said:**
> Is this an external drive you want to use for data and as asked above, what filesystem type is it?  When you ran the chown command, were you in the directory immediately above new_drive and did that mount point actually exist.  Is this a partition on the drive or just a single directory?

No, it's not an external drive.  The file system is fat32.

---

### Post by yancek on 2024-06-24
>  /dev/sdb1      vfat   299G     46G  253G   16% /home/claus/neue_Platte -> this ist the harddrive

That is your problem.  The output shows your /home partition is on the first partition of the second drive (sdb1) with a vfat filesystem.  That is a foreign (windows) filesystem and I do not know why you would expect that to work or how it was done.  The default filesystem for Ubuntu is ext4 but in any case, you need a Linux filesystem as a windows filesystem will not work.  Also the standard owner/permission used on Linux are not usable with a windows filesystem.  The only use of a vfat filesystem on current computers with Linux is vfat for the EFI partition which you show on the other drive.  I don't know how you got your /home partition on a vfat drive but if you can, try to access the data on that partition and copy it somewhere else so you can reformat that partition with ext4.  Formatting will overwrite any data on it.

---

