---
title: "Re-naming partitions on Desktop"
date: 2008-07-26
forum: General Help
---

### Post by dalziel on 2008-07-26
I have a spare HDD partitioned into several drives, all NTFS. They all automount, and show on the desktop. However, their displayed names on the desktop, are not what I want. eg one drive mounted at /media/Data, which is the name I want, shows as '25.8 GB Media'. Within Nautilus (or any other file browser), under File System/media, the drive shows as 'Data'. Some of them do show the name I want eg /media/Music shows as 'Music'. The drive was originally partitioned in a WinXP environment, but the 28.5 GB media one was subsequently resized in Ubuntu. How do I change the name of the drive displayed on the desktop?

---

### Post by cariboo on 2008-07-26
THe easiest way is start up Windows and go into Control Panel-->Administative Tools-->Computer Management-->Disk Management and just add labels to your partitions. If you don't have a Windows partiton, you can use ntfslabel which is part of ntfs-progs

Jim

---

### Post by Herman on 2008-07-26
I agree with cariboo907, and here are the commands if you need to do it from Ubuntu,
```
sudo apt-get install ntfsprogs
``````
ntfslabel -v /dev/sda1 DATA
```Where '/dev/sda1' is the partition that contains the NTFS file system you want to set a label for. Check with 'sudo fdisk -lu' or look with Gnome Partition Editor to make sure.

I think the latest versions of GParted Live CD also support labelling most file systems.

Regards, Herman :)

---

### Post by unutbu on 2008-07-26
Partitions which are automounted are mounted in directories whose names match the volume label. To change the volume label on NTFS partitions:

Install the ntfsprogs package.
Open a terminal and type

```
sudo ntfslabel DEVICE LABEL
```

Where DEVICE is the partition's device name, e.g. /dev/sdb1
and LABEL is a string like Data or Music.

This information comes from [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Edit: Hello cariboo907 and Herman! Sorry; I didn't realize you two had already posted.

---

### Post by dalziel on 2008-07-26
Thanks for all your help so far. However, unless I am doing something wrong, this is not working. I have installed ntfsprogs, unmounted the volume, and run the script as suggested. The volume is correctly labelled in File system/media/, but the name attached to the volume on the desktop is still as before ie '25.8 GB media' and not 'Data'. I don't have Windows on this machine, so can't follow your suggestion cariboo907. If all else fails, I will have to remove the drive and put it in a Win machine - admitting defeat!! It is really of little moment, but just annoying to me that I cannot do what I want with it yet. Once again, thanks for your replies.

---

### Post by unutbu on 2008-07-26
Okay, try this:
Right-click on the icon of the partition on the Desktop. Select 'Properties'. Click on the Volume tab.
Click on the triangle next to 'Settings'. Fill in the text field next to 'Mount Point:'. If you put 'music' in the text field, then the partition should mount at /media/music and show up on the desktop as 'music'.

The change will not take effect until the partition is remounted. So unmount the partition and then run the following command:
```

sudo /etc/init.d/hal restart
```
This will cause HAL to try to automount the partition again.

---

### Post by dalziel on 2008-07-27
Thanks again. This is becoming a battle of wills between myself and the computer. I had already got to your suggestion about the mount point in properties/settings but not the HAL restart, I had just been unmouting through root, and then remounting. FSTAB and MTAB both show what I would expect ie 
/dev/sdb5 /media/Data ntfs-3g defaults,locale=en_AU.UTF-8 0 0
and
/dev/sdb5 /media/Data fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
respectively. However, it is still showing the same on the desktop - '25.8 GB Media'!

---

### Post by kaibob on 2008-07-27
This has been an issue since Hardy alpha. Labeling the drive/partition works for most--not sure why it doesn't for you. Some additional information:

[https://wiki.ubuntu.com/DesktopVolumesRepresentation](https://wiki.ubuntu.com/DesktopVolumesRepresentation)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366)

---

### Post by dalziel on 2008-07-27
Again, thanks for all your help. I read those last two refs, and obviously people a lot brighter than me (most of the world!) are working on this (to me) very small problem.
I am amazed at how quickly responses arrive to queries - very heartening.

---

