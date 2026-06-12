---
title: "upgrade ubuntu 10.10 doesn't mount my external drive"
date: 2011-04-14
forum: Hardware
---

### Post by YaStrannik on 2011-04-14
I did a clean upgrade from Ubuntu 10.04 and now I have this problem. My new Ubuntu 10.10 fails to show me the contents of my external hard drive with any consistency. Sometimes it does (especially when I reboot the computer) and then it doesn't. When I look into the Disk Utility, I see this:

Drive: ST932032 5AS
Firmware Version: 0100
Location: -
Write cache: - 
Partitioning: Master Boot Record

Device: /dev/sdb

Connection: USB at 480.0 Mb/s


Usage: Filesystem
Partition type: HPFS/NTFS
Type: FAT (32-bit)

Device: /dev/sdb1

Mount point: Not Mounted

If I try to Mount Volume, I get this:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed"

What is this about? What can I do about it? Thanks!


PS. PROBLEM SOLVED USING [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by mactrent on 2011-04-14
YaStrannik,

I'm having the exact same problem, and I figured out that this is device name-specific.  If I plug in another USB and mount it as sdb, then mount the one I want as sdc, I can access it.

I'd assume that there's another application that's using the name somehow, but don't know what that might be.

Given this additional knowledge, can anyone give us a more permanent solution?

---

