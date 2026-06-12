---
title: "Hard drive - Something very odd..."
date: 2018-11-15
forum: Hardware
---

### Post by Shugs81 on 2018-11-15
so...

I just discovered steam play... I tried to run my games and it just did the "Starting" thing it does then it cut off...

I read that it has issues with partitions over 1tb... I tried to make a new partiton on one drive and it just didn't like it... I used the Disks utility to resize a partition and create a new ext4 one in the space...

it went a bit odd and wouldn't mount it... so i deleted it and made the partition on another drive using gparted... which worked ok (apart from not making me the owner... i'll sort that later...)

I ran blkid and this was what i got...

```
[sudo] password for shugs81: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="Recovery" UUID="5A32197D32195EF7" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="7542110c-49eb-49af-b71d-d4f2892e7eba"
/dev/sda2: UUID="8A1B-A08F" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6fd2e14c-af19-4f3c-a00f-5408f5c3c5c7"
/dev/sda4: UUID="44CE2AAFCE2A98E6" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e12556b5-c17c-4a52-a089-833c0672adb0"
/dev/sdb1: UUID="1C04-12A4" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e6936905-6173-4666-b464-d8c904cf6469"
/dev/sdb2: UUID="f40de758-15fc-43d7-a999-852510004a2f" TYPE="ext4" PARTUUID="e87865b1-8a01-4279-ad19-3424420bd4c8"
/dev/sdc1: UUID="01D4359C767DC030" TYPE="ntfs" PARTLABEL="Test Partition" PARTUUID="95f274e3-9446-89fb-84cf-a8a214d3c416"
/dev/sdd1: UUID="F40215000214CA0E" TYPE="ntfs" PARTUUID="71987caf-a350-2949-fe4d-6ba6215735ce"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"
/dev/loop30: TYPE="squashfs"
/dev/loop31: TYPE="squashfs"
/dev/loop32: TYPE="squashfs"
/dev/loop33: TYPE="squashfs"
/dev/loop34: TYPE="squashfs"
/dev/sda3: PARTLABEL="Microsoft reserved partition" PARTUUID="a3ca856e-acac-4aca-af4d-59707a93ed5a"
/dev/sdd2: UUID="ae956687-b6fe-4fea-8c93-b10db4fe70a4" TYPE="ext4" PARTUUID="8ff8be0e-b24d-4875-88c6-99f83ecc5acd"

```

what the hell have i done???? and how do i sort it?

Thanks! :D

---

### Post by TheFu on 2018-11-15
I have no idea, but you can safely ignore the "loop" entries.  Those are part of the new snap package distribution method. Unless the issue is directly related to 1 of those package or a loop device that you manually created.   Almost always, the loop devices can be ignored.

The manual steps to create a partition are:
* use a partitioning tool to make a partition.
* use a file system formatting tool to lay down the file system type you want. EXT4 is a good general choice, if you don't have specific different needs.
* manually mount the file system to any empty directory you like - this is a "mount point"
* change the permissions on the newly mounted partition to whatever you need. I generally leave the top level owned by root:root, then create subdirectories for any specific userids to manage, but do whatever you need.
* if the new storage is a permanent mount over eSATA or SAS or SATA connections, then I'll modify the /etc/fstab to make it available automatically.
* if the new storage is portable or temporary or over USB, then I'll configure the mount to happen via autofs.  USB connections are flaky in my experience, hence the reason I use autofs.  I actively prevent automatic mounting using GVFS that is part of any gnome tool.

I've never used gnome-disks, but I use gparted, fdisk, parted for these different needs.  **Gparted** is the easiest and can both create a new partition AND format it with some file systems.  I don't think it supports modifying the fstab or helping with a manual mount.  But gparted only works on desktops, not servers, which don't have a GUI.

I have seen a number of forum posts here where people find a GUI tool to mount storage, but then find the performance to be poor.  Often, there are a number of interactions involved.  Using NTFS and using GVFS to manage the mount will often lead to terrible performance.  The NTFS driver is a FUSE one, which doesn't run in kernel space. For a number of reasons, it is slow.  There is something about GVFS mounts that cause them to be slow.  I saw a kernel patch for 4.20 kernel [https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.20-FUSE](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.20-FUSE)  a few weeks ago that is supposed to make those types of mounts faster, but how much faster wasn't included.  There have been multiple performance improvements, it seems.  Now we just need to wait for that kernel to make it to our systems sometime next year.

In the meantime, to get the best performance,
* use ext3/ext4 file systems for storage
* avoid using a GUI to mount this storage. Once mounted, you can use a GUI.

Clear as mud?

To help others help you more easily, please edit your post above and remove all the lines with "loop".

---

### Post by Shugs81 on 2018-11-15
it was the loop entries i was wondering about... if they don't mean anything then that's good!! :D

---

