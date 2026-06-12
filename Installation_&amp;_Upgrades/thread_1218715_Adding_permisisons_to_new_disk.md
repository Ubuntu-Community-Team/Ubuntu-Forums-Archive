---
title: "Adding permisisons to new disk"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by abasel on 2009-07-21
I am using Ubuntu Desktop 9.4.

After reading various posts, I have managed to auto mount my 2nd disk.

I can however not create any folders or save to it; only browse.

I have tried the following but it doesn't seem to do anything

sudo chgrp users /media/disk-1
sudo chmod g+w /media/disk-1
sudo chmod +t /media/disk-1

Basically I want any user to be able to access and write or delete from the disk

Any ideas

---

### Post by merlinus on 2009-07-21
```
gksu nautilus
```

Navigate to the mountpoint, rightclick, properties, permissions.

---

### Post by philcamlin on 2009-07-21
> **merlinus said:**
> ```
gksu nautilus
```Navigate to the mountpoint, rightclick, properties, permissions.

+1 that should work

---

### Post by abasel on 2009-07-21
Still no joy, when I try change the group from root to users I get told that I don't have permission.. even when logged on as root.

I've tried making changes to the other options but doesn't appear to work. Are you able to give me more details?

Cheers

---

### Post by spcwingo on 2009-07-21
Try this:

```
sudo chown /mount_point your_user_name:your_group -rwxrwxrwx
```

This should allow read, write and executable permissions for owner, group and all others.

---

### Post by merlinus on 2009-07-21
What is the filesystem?

If spcwingo's suggestion does not work, you might try unmounting the partition, and then changing permissions with

```
gksu nautilus
```

---

### Post by abasel on 2009-07-21
> **spcwingo said:**
> Try this:

```
sudo chown /mount_point your_user_name:your_group -rwxrwxrwx
```

This should allow read, write and executable permissions for owner, group and all others.

But this will do it for a certain user, I want it to apply to all users in the "Users" group.

---

### Post by spcwingo on 2009-07-21
> **abasel said:**
> But this will do it for a certain user, I want it to apply to all users in the "Users" group.

Did you see the second part of my post?

> This should allow read, write and executable permissions for owner, group and all others.

---

### Post by abasel on 2009-07-21
When I do

chown /media/disk-1 sysadmin:users -rwxrwxrwx

I get 

chown: invalid option --'r'

I am using ubuntu 9.04

---

### Post by abasel on 2009-07-21
Finally got it using nautilus.

What I was doing wrong was trying to set permissions on the mounted disk, instead of unmounting it and then going to the actual mount point.

I would like to know what I was doing wrong with the chown command though.

Cheers and thanks for your patience.:popcorn:

---

### Post by merlinus on 2009-07-21
You cannot change permissions on a non-linux filesystem if it is mounted.  Perhaps that was the problem.

---

### Post by abasel on 2009-07-21
:(

Aaagh so it did not work. I must have been in an admin console.

I know it's not difficult... but have no idea what I'm doing wrong

---

### Post by merlinus on 2009-07-21
What filesystem does this use?  You probably can add a line in /etc/fstab to mount the partition and set the permissions automatically.

Also, what partition is it, e.g. sdb2, and what mountpoint have you created?  If you are not sure, post results of

```
sudo fdisk -l
df -h
```

---

### Post by abasel on 2009-07-21
The disk in question is sdb1

fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d51ad4a8-96b1-4ff8-8bf4-10c21feee722 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=843f424d-63c3-48ce-938b-356e45fba684 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/disk-1   vfat    rw,user 0       0

```


root@vmware:~# fdisk -l
```

Disk /dev/sda: 73.4 GB, 73404514304 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1baf1baf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8555    68718006   83  Linux
/dev/sda2            8556        8924     2963992+   5  Extended
/dev/sda5            8556        8924     2963961   82  Linux swap / Solaris

Disk /dev/sdb: 293.6 GB, 293628542976 bytes
255 heads, 63 sectors/track, 35698 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c0b1c0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       35698   286744153+  fd  Linux raid autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
81 heads, 63 sectors/track, 61254 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0xee0a5d5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       61255   156290872+   7  HPFS/NTFS

```

---

### Post by merlinus on 2009-07-21
/dev/sdb1               1       35698   286744153+  fd  Linux raid autodetect

This line seems strange to me, since sdb1 is a fat32 filesystem, but linux is reporting it as linux raid autodetect.

---

### Post by abasel on 2009-07-22
As you will gather... Linux is not my forte... currently there is no data on the drive in question. I am quiet happy to reformat (would like it to be fat32 though so that I can still access it if my OS crashes) I just want the permissions fixed so that I can save to it.

I just need to know how :-)

---

### Post by merlinus on 2009-07-22
Why not ntfs?  Linux has no problem reading and writing to that filesystem.  It is also somewhat less prone to fragmentation, and can handle larger file sizes.

You can then install ntfs-config, which will give you a gui that will write the correct info to /etc/fstab.

---

### Post by abasel on 2009-07-22
K that's fine. I would prefer to do it from the command line. Up to now I have used the Linux partition GUI.

Could you give me the command?

---

### Post by merlinus on 2009-07-22
parted will not create an ntfs partition, but you can use it for fat32.

Why not use gparted?

---

### Post by abasel on 2009-07-22
I did use gparted, but will do so again, this time using NTSF.

Will have to do so tomorrow 5:12pm in NZ and I need to get my son home.

---

### Post by abasel on 2009-07-22
I've now installed ntfs-3g using [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

I've deleted my initial Fat32 partition but when I try to created the NTFS permission, the NTFS option is grayed out

---

### Post by merlinus on 2009-07-22
Can you be more specific?  For example, are you trying to format the partition as ntfs, and if so, are you using gparted?

---

### Post by abasel on 2009-07-22
K.. got NTFS working, had to run

sudo apt-get install ntfsprogs

---

