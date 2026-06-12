---
title: "Xubuntu 13.04: &quot;Checking Disk Drives for Errors&quot;"
date: 2013-05-13
forum: Hardware
---

### Post by ipeters61 on 2013-05-13
Hello Ubuntu community,

I have a relatively fresh install of Xubuntu 13.04 on one of my desktops (see specs below), and it has an issue when booting.  It's not necessarily a bad thing (I don't think), but it's definitely a nuisance.

Every time I boot the system, ever since the installation, it says that it is "Checking disk drives for errors.  This may take several minutes.  Press C to cancel all checks in progress.  Routine disk drive check."

I have always shut down this system cleanly (i.e.: through the shut down command in the Xfce desktop), so I don't get why this is happening.  I have read that ext2 partitions are *always *checked for some reason or another (I can't remember my original source, but I know the ext3 Wikipedia page says that it's normal behavior for ext2 filesystems).

The partition layout of the system is a 125 MB /boot partition (ext2), a ~75 GB / partition (ext2), and a ~4 GB swap partition.

The system's specifications are: Intel Pentium 4 @ 2.0 GHz, 1.25 GB DDR-400 Memory, 80 GB Maxtor 4D080H4 Hard Drive, and Intel 845 Graphics.

I am assuming that this is due to the ext2 file system.  I chose an ext2 file system because I was under the impression that journaling file systems slow down the system overall (however, my server uses ext3 and my laptop uses ext4, because they are newer systems than this one).  However, if that shouldn't be the case (i.e.: if journaling file systems don't actually slow down the system), is there an easy way to convert the partition to ext3/ext4, or am I better off with ext2?  Or is there a way around the every-boot disk check?

Thank you in advance for any help.

---

### Post by landersohn on 2013-05-15
I had a similar problem a while back with a certain kernel version: this kernel caused some file system errors at shutdown and a subsequent slow boot. Forgot which kernel version it was but upgrading the kernel fixed my problem.

---

### Post by ipeters61 on 2013-05-15
I decided to upgrade to ext3.  I tried upgrading the kernel, rebooted a few times, and it didn't seem to help, unfortunately.

I am under the assumption that the ext2 file system inherently requires a filesystem check on each boot.  I converted to ext3 using this guide: [https://wiki.archlinux.org/index.php/Convert_ext2_to_ext3](https://wiki.archlinux.org/index.php/Convert_ext2_to_ext3).  I rebooted a few times after that and the filesystem checks went away.

---

### Post by Michael_J_OLeary on 2013-10-16
> **ipeters61 said:**
> Hello Ubuntu community,

I have a relatively fresh install of Xubuntu 13.04 on one of my desktops (see specs below), and it has an issue when booting.  It's not necessarily a bad thing (I don't think), but it's definitely a nuisance.

Every time I boot the system, ever since the installation, it says that it is "Checking disk drives for errors.  This may take several minutes.  Press C to cancel all checks in progress.  Routine disk drive check."

I have always shut down this system cleanly (i.e.: through the shut down command in the Xfce desktop), so I don't get why this is happening.  I have read that ext2 partitions are *always *checked for some reason or another (I can't remember my original source, but I know the ext3 Wikipedia page says that it's normal behavior for ext2 filesystems).

The partition layout of the system is a 125 MB /boot partition (ext2), a ~75 GB / partition (ext2), and a ~4 GB swap partition.

The system's specifications are: Intel Pentium 4 @ 2.0 GHz, 1.25 GB DDR-400 Memory, 80 GB Maxtor 4D080H4 Hard Drive, and Intel 845 Graphics.

I am assuming that this is due to the ext2 file system.  I chose an ext2 file system because I was under the impression that journaling file systems slow down the system overall (however, my server uses ext3 and my laptop uses ext4, because they are newer systems than this one).  However, if that shouldn't be the case (i.e.: if journaling file systems don't actually slow down the system), is there an easy way to convert the partition to ext3/ext4, or am I better off with ext2?  Or is there a way around the every-boot disk check?

Thank you in advance for any help.




ext2/ext3 are slower then ext4   ext2 is your prob with the checking every boot mine did that too but any newer linux any 2013+ should work ext4  fine i have tested it with almost all them no probs with none beside few kinds missing the drivers/tools to keep it in good shape found xubuntu/fedora/mint best 3 but x is best for all but not wise to convert from ext2/3 to another and ext4 cant be changed with out major probs so best just back up all u stuff u want to keep do fresh install  useing ext4 u if u got more then 1gig ram u dont really need a swap but best keep a under 2gig swap i use 1536mb though system never touchs it xubuntu good for that

---

