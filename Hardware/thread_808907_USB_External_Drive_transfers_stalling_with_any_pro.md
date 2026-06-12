---
title: "USB External Drive transfers stalling with any protocol"
date: 2008-05-26
forum: Hardware
---

### Post by appleijunkie on 2008-05-26
Running Ubuntu 8.04 Server, using a SATA to USB adapter with a 80GB 2.5" HDD formatted as ext3, and here's what's up:

Any time I attempt to transfer any file *from* the external drive to a remote machine - Windows, Mac, or another Linux install - using either Apache, Samba, SCP, or SFTP the transfer starts out at roughly 2MB/s and immediately drops out to around 15KB/s or so. I actually get a -stalled- message when doing this with SCP. On the flip, if I copy a file from my internal drive, no issues at all. So, in my mind at least, I don't feel that I'm dealing with any type of network-related issues, right? Also, I have another known good adapter I use almost daily with work that I tried, and I get the same issues, so that rules out the possibility of hardware issues. The hard drive has not reported any SMART errors, and FSCK comes back clean. Transfers from the external drive to the internal also are very slow/stalling as well.

So, I ask, what am I missing??? I'd appreciate any pointers at all. Below, I am including an output of my fstab just in case it helps. Thanks in advance, really!:confused:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=cdd82d2e-5d16-4f85-8043-1c53352f557e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=79279e7e-e50e-49dd-b36d-978afb7ddda3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
[COLOR="Red"]/dev/sdb1	/mnt/usb	ext3	defaults	0 	0[/COLOR] <--HDD in question

---

