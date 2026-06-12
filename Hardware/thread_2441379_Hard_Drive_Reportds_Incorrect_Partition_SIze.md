---
title: "Hard Drive Reportds Incorrect Partition SIze"
date: 2020-04-23
forum: Hardware
---

### Post by rsteinmetz70112 on 2020-04-23
I have a relatively new hard drive I pulled from a machine. I think it was originally part of an array. I loaded it into a external USB enclosure and firing it up.
The Drive is a 1 TB Toshiba drive but  gparted and gnome-disks give really odd results.  

Starting gparted from a terminal I get this message:
```

gparted
Unit -.mount does not exist, proceeding anyway.
======================
libparted : 3.2
======================
Can't have a partition outside the disk!
```

Gparted reports sdb as 931.51GiB but reports partition sdb1 as 7.25 TiB.
Gparted has the following warning:
```
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sdb1 is missing
```
boot and raid flags are set.
Obviously something is wrong.
Is there a reasonable way to see if the drive has anything usable in it?

---

### Post by CelticWarrior on 2020-04-23
Do you want to recover something from it - extremely unlikely - or just reuse it?

---

### Post by rsteinmetz70112 on 2020-04-23
It was  unused for a while so I want to find out if there is anything on it.
I'm also curious since I've never encountered this before.

---

### Post by yancek on 2020-04-23
What do you get running:  fdisk, gdisk or parted, anything useful?  The filesystem is damaged so the first thing to try is to repair that but if you don't know what filesystem is/was on the disk that won't work.

---

### Post by oldfred on 2020-04-23
RAID normally has meta-data on it that has to be removed before use as regular drive.
Not sure then if you lose all data that you may be looking for?

[https://unix.stackexchange.com/questions/411206/how-to-wipe-md-raid-meta](https://unix.stackexchange.com/questions/411206/how-to-wipe-md-raid-meta)

dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.

I have this old command in my notes, but have never used RAID.
sudo dmraid -E -r /dev/sdX #where sdX is your drive
You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by rsteinmetz70112 on 2020-04-23
> **yancek said:**
> What do you get running:  fdisk, gdisk or parted, anything useful?  The filesystem is damaged so the first thing to try is to repair that but if you don't know what filesystem is/was on the disk that won't work.

I get pretty much the same think I get from the other utilities. The partition is bigger than the disk.

I'm pretty sure the disk was part of a raid 1 array possibly with lvm on top of it.

Seems like the thing to do is try to repair the partition table. I seem to remember that you can rewrite the partition table without destroying the underlying filesystem and date. But I a little fuzzy on how.

---

### Post by CelticWarrior on 2020-04-23
With lvm and part of a RAID don't bother trying to recover anything from that.

---

### Post by rsteinmetz70112 on 2020-04-23
> **oldfred said:**
> RAID normally has meta-data on it that has to be removed before use as regular drive.
Not sure then if you lose all data that you may be looking for?

[https://unix.stackexchange.com/questions/411206/how-to-wipe-md-raid-meta](https://unix.stackexchange.com/questions/411206/how-to-wipe-md-raid-meta)

dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.

I have this old command in my notes, but have never used RAID.
sudo dmraid -E -r /dev/sdX #where sdX is your drive
You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

OK I'm positive that mdadm was used to create the raid array. I checked and madam was not installed on this machine. I installed it, that may help decipher the drive.

---

