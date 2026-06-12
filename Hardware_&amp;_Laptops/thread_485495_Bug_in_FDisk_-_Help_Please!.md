---
title: "Bug in FDisk - Help Please!"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by LinuxLovesMJ on 2007-06-26
I am using ubuntu 7.04 fiesty. I recently installed a new harddrive and cannot get it to work. In fdisk, it recognizes the harddrive when I type fdisk -l, but for some reason it shows that the new harddrive has a partition named "Linux LVM." I have no clue how this is possible because I have never created any partitions on this harddrive...I just installed it.

Heres my outputs from terminal, hope this helps, and thank you for your replies:

FDISK -l

```

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401   8e  Linux LVM

```

---

### Post by PaulFr on 2007-06-27
Then you may want to start with **gparted** to delete all partitions and create the ones you want (see **[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)** for details). Similarly if you want to use fdisk, you should first clear the partition table and then create the partitions you need.

---

