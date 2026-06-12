---
title: "File system corruption in Ubuntu 12.10 while using Super Top M6116 SATA Bridge"
date: 2012-11-19
forum: Hardware
---

### Post by ptsubin on 2012-11-19
I have the following system.
Laptop: Dell Inspiron 1525
OS: Ubuntu 12.10 32bit

I have connected a 2.5 Inch internal Hitachi 250GB HDD using Super Top M6116 SATA Bridge to the system. Was copying files from the device (Didn't write anything to it at all) and got I/O error after a while. Gave sync, unmounted the device and plugged again. All the partitions are detected but none would mount. fsck will not fix it even if I specify the superblocks pointed by mkfs.ext4 -n. parted, gparted, mkfs none would format the drive or any partitions. The device worked perfectly fine Under ubuntu 12.04 running on a samsung laptop and 12.04 live cd on the same system. Works fine in windows. As the data was already lost I have tried creating a partition under windows. Format it and then plug it to 12.10 in the same machine. Unmount it and plug it again. Got the same error. chkdsk won't fix the file system (I was finally trying ntfs too).

Saw similar issue listed here: [https://bbs.archlinux.org/viewtopic.php?pid=1189026](https://bbs.archlinux.org/viewtopic.php?pid=1189026)

I guess this is an Issue with Linux-3.5. Saw the same issue mentioned in the above link for linux-3.6 also. Is this a know issue? Is there a workaround for this?

---

### Post by Peltsi on 2012-11-19
Hi,

I wonder if my problem is related to this (thread: [http://ubuntuforums.org/showthread.php?t=2084771](http://ubuntuforums.org/showthread.php?t=2084771)).. I just ran lsusb to see what my usb-sata converter is and it's also super top M6116 SATA bridge. Same VID&PID as mentioned in the arc-linux forums 14cd 6116. Running 3.2.0-33-generic & Xubuntu 12.04

It sounds like the corruption problem is related closely to this one adapter chip.

---

### Post by ptsubin on 2012-11-21
It seems that way. But mine works fine in Ubuntu 12.04 and Windows. 12.10 seems to have problem with it..

---

