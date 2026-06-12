---
title: "mdadm and partition trouble"
date: 2017-04-11
forum: Hardware
---

### Post by clarknova on 2017-04-11
Ubuntu 16.04.2 amd64

My system boots from SSD (sda), and I have two disks (sdb and sdc) whose only job is to be part of a jbod/linear array. I don't care about speed or redundancy as much as I care about power saving, so that's why jbod. I created the array around a month ago and have been recording streaming camera video to it since. As far as I can tell, the array is working fine.

The trouble, then, is that when I open gparted, or apply any operation in gparted, it complains "Invalid partition table on /dev/sdc -- wrong signature 8fbc." and I have to click "Ignore" to proceed. I also noticed the old partitions that were on sdc (from an ESXi system) appeared on the desktop, but greyed out. It appears that the old partitions from sdc are still remembered on the disk, and it's causing some confusion to certain utilities.

Is this problem potentially harmful beyond the annoyance? Is there a way to resolve it without backing up or losing all of the data on the linear array? It wouldn't be a huge problem to lose the data, but I prefer not to destroy it when an alternative can be found.

```
root@desk:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active linear sdc[1] sdb[0]
      1953263024 blocks super 1.2 0k rounding
      
unused devices: <none>
```

```
root@desk:~# sfdisk -d /dev/sdb
label: dos
label-id: 0x84b17240
device: /dev/sdb
unit: sectors

/dev/sdb1 : start=        2048, size=  1953521664, type=83
```

```
root@desk:~# sfdisk -d /dev/sdc
Ignoring extra data in partition table 6.
Ignoring extra data in partition table 6.
Ignoring extra data in partition table 6.
Invalid flag 0xbc8f of EBR (for partition 6) will be corrected by w(rite).
label: dos
label-id: 0x33745b32
device: /dev/sdc
unit: sectors

/dev/sdc1 : start=        8192, size=     1835008, type=5
/dev/sdc2 : start=     1843200, size=     8386560, type=e
/dev/sdc3 : start=    10229760, size=   458633216, type=fb
/dev/sdc4 : start=          32, size=        8160, type=4, bootable
/dev/sdc5 : start=        8224, size=      511968, type=6
/dev/sdc6 : start=  1087209248, size=    67155336, type=df
```

---

