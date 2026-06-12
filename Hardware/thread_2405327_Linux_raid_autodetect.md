---
title: "Linux raid autodetect"
date: 2018-11-04
forum: Hardware
---

### Post by sed_faster on 2018-11-04
Hello folks,

I have this two disc connect in same PATA cable:

1 (master)-[https://snag.gy/XIQKTP.jpg](https://snag.gy/XIQKTP.jpg)
2 (slave)-[https://snag.gy/UaXRiz.jpg](https://snag.gy/UaXRiz.jpg)

When I turned my ubuntu server and tried mount the slave disc I receive this error:
```

$ df -kh
Filesystem      Size  Used Avail Use% Mounted on
udev            179M     0  179M   0% /dev
tmpfs            42M 1020K   41M   3% /run
/dev/sda2        38G  3.2G   33G  10% /
tmpfs           209M     0  209M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           209M     0  209M   0% /sys/fs/cgroup
/dev/loop0       88M   88M     0 100% /snap/core/5662
/dev/loop1       87M   87M     0 100% /snap/core/4486
/dev/loop2       88M   88M     0 100% /snap/core/5742
tmpfs            42M     0   42M   0% /run/user/1000
as@as:~$ ls
disk2
as@as:~$ sudo mount /dev/sdb1 disk2/
[sudo] password for as: 
mount: /home/as/disk2: unknown filesystem type 'linux_raid_member'.

```

Also I don't know why the report the command fdisk -l it is very large:
```

$ sudo fdisk -l
Disk /dev/loop0: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 87.9 MiB, 92114944 bytes, 179912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 38.2 GiB, 40982151168 bytes, 80043264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C680C420-CDF9-42E2-A5D6-302B07F30205

Device     Start      End  Sectors  Size Type
/dev/sda1   2048     4095     2048    1M BIOS boot
/dev/sda2   4096 80039935 80035840 38.2G Linux filesystem


Disk /dev/sdb: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0006a790

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 312580095 312578048 149.1G fd Linux raid autodetect


```

More information about my system:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
as@as:~$ uname -a
Linux as 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Should I try format the sdb1 as ext4? I yes, how should I proceed?
Thanks

---

### Post by TheFu on 2018-11-04
At some point, the disk was included in a RAID set.  You need to overwrite that data. Doubtful that a format (mkfs on Linux) will overwrite the necessary areas.  There are different sorts of RAID controlled by software, hardware or Fake-RAID, so the right tool needs to be used to clean up the "I'm in a RAID set" marker that is on the disk.

BTW, all the "loop" devices are thanks to the new Snap.io package distribution method.  If you are working with storage, it is safe to completely ignore those entries.  Snaps are not required, btw.  You can purge those and install the non-snap versions if you like. I have no clue why a calculator needs to be in a Snap.  I could be convinced that a web browser needs to be in a snap for security, assuming the settings for the snap actually confine the program sufficiently.  Canonical seems to have gone snap-happy to me.

---

### Post by sed_faster on 2018-11-04
Should I try use mkfs in this disc?
Thanks

**[UPDATE1]**
I tried execute this commands:
```

Disk /dev/sdb: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0006a790

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 312580095 312578048 149.1G fd Linux raid autodetect
as@as:~$ sudo mkfs -t ext4 /dev/sdb1
mke2fs 1.44.1 (24-Mar-2018)
/dev/sdb1 contains a linux_raid_member file system labelled 'sef:0'
Proceed anyway? (y,N) y
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
as@as:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted.
as@as:~$ sudo mkfs -t ext4 /dev/sdb1
mke2fs 1.44.1 (24-Mar-2018)
/dev/sdb1 contains a linux_raid_member file system labelled 'sef:0'
Proceed anyway? (y,N) y
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!

```
But I haven't success!

---

### Post by TheFu on 2018-11-04
I said:
>  There are different sorts of RAID controlled by software, hardware or Fake-RAID, so the right tool needs to be used to clean up the "I'm in a RAID set" marker that is on the disk.

mkfs is the way that "formatting" is done on Linux.  I said: 
> At some point, the disk was included in a RAID set. You need to overwrite that data. Doubtful that a format (mkfs on Linux) will overwrite the necessary areas. 

I don't recall the names of the programs to remove the metadata on the disk that reports it is **part of a RAID**. Until you clear that flag, all the tools will complain.  Google should find those tools. Sorry that I don't know them.  I use them once a decade.  For software RAID, I think mdadm can do it.  For hardware RAID, it will be part of the HW RAID software and for fake-RAID - I haven't a clue. Never saw the point of using Fake-RAID.

---

### Post by sed_faster on 2018-11-04
Thanks @TheFu to your help. I really don't know how should I handle this situation. Tomorrow I will read more deep this article [https://www.tecmint.com/manage-software-raid-devices-in-linux-with-mdadm/](https://www.tecmint.com/manage-software-raid-devices-in-linux-with-mdadm/) maybe it is will helpful to me. Thanks any way.

---

