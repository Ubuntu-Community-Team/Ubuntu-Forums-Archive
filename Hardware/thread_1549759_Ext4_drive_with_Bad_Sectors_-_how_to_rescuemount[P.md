---
title: "Ext4 drive with Bad Sectors - how to rescue/mount?[Permission Denied when accessing]"
date: 2010-08-10
forum: Hardware
---

### Post by vcppp_p on 2010-08-10
Him
I have an 500GB SATA drive:
> 
 * 50 GB Ext4 Filesystem [sda1]
 * 450GB Extended:
   * 5 GB Swap [sda5]
   * 300GB Ext4 [sda6]
   * 145 GB Ext4 [sda7]


I'm running the Ubuntu 10.04 LiveUSB, than trying to mount the disk.
The first (50GB) filesystem mounts ok, but when I'm trying to mount 300GB or 145GB partitions, it seems to mount ok but than throws "Permission Denied" when trying to access...

```

ubuntu@ubuntu:~$ sudo mkdir /media/abc/
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/abc
ubuntu@ubuntu:~$ cd /media/abc
bash: cd: /media/abc/: Permission denied

```

Any solutions?!

Palimpset Disk Utility reports:
 107 Reallocated Sectors
 2 Current Pending Sectors

---

### Post by Fafler on 2010-08-10
sudo bash
cd /media/abc

Bad practice, but i just might work.

---

### Post by PresenceofMind on 2010-08-11
If it get really bad, try testdisk:

```
sudo apt-get install testdisk
```

---

