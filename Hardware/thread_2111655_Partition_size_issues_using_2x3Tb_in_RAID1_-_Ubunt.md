---
title: "Partition size issues using 2x3Tb in RAID1 - Ubuntu 12.10"
date: 2013-02-02
forum: Hardware
---

### Post by atudoll on 2013-02-02
Hello,

I've installed a new nas/media center with Ubuntu 12.10with the following configuration :
 - Mother board : ASUS F2A85-M LE (supposed to manage directly RAID1)
 - Ubuntu 12.10 installed on an SSD
 - 2x 3Tb that I would like to use for storage and home directories

So, in a first time I tried to use the RAID1 proposed by the mother board, I created it successfully, the bios seeing it correctly.
Once Ubuntu started, I don't see the RAID disk anymore, I see 2 distinct disk of 3Tb each.

I finally disabled the RAID from the mother board and switched to a software RAID.
To do that, I've :
 - created a GPT partition table on each disk (using GParted)
 - created an ext4 partition of 3Tb on each (using parted)
 - build the array to create the RAID volume (using mdadm)
 - finally mounted it in /home

This works perfectly except that when I mount the volume, it has a capacity of 2Tb.
```

root@ubuntu:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        48G  3.7G   42G   9% /
udev            3.6G   12K  3.6G   1% /dev
tmpfs           1.5G  924K  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.6G  164K  3.6G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/md126      2.0T  184G  1.7T  10% /home

```

There is the entry in /etc/fstab :
```
UUID=6508d199-5bdf-464f-b492-bfa69f3ea79f /home         ext4    defaults        0       2
```

Does anyone have any idea ? :confused:

---

