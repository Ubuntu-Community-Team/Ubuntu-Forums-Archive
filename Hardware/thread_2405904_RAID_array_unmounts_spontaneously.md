---
title: "RAID array unmounts spontaneously"
date: 2018-11-13
forum: Hardware
---

### Post by clarknova on 2018-11-13
Ubuntu Server 16.04

I have a client system with a 2-device RAID0 array that mounts at boot with fstab. After some uptime, generally a few days, the array is unmounted and I have been unable to get it to remount without rebooting the server. This is a problem. Any insight on troubleshooting this? I will attempt to post what appears relevant, then I will have to reboot this system to get the array back online.

```
root@ubuntu-nvr:/home/clarknova# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Apr 20 11:32:48 2017
     Raid Level : raid0
     Array Size : 7813774336 (7451.80 GiB 8001.30 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Apr 20 11:32:48 2017
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 512K

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync
       1       8       16        1      active sync


```
```
root@ubuntu-nvr:/home/clarknova# blkid
/dev/nvme0n1p1: LABEL="ROOT" UUID="0265d652-3271-454e-a615-735969e4d8da" TYPE="ext4" PARTLABEL="ROOT" PARTUUID="7f77e7e0-17e1-4192-b1e3-f097f5e722b9"
/dev/nvme0n1p2: LOGUUID="2c5b6825-3b76-4fb6-bfa4-d8a533c7734d" TYPE="xfs_external_log" PARTLABEL="JOURNAL" PARTUUID="57be3812-87f1-49b8-ae4c-16f899d01c3c"
/dev/nvme0n1p3: UUID="29a54ab1-32c1-40db-9196-13c223b7150f" TYPE="swap" PARTLABEL="SWAP" PARTUUID="37ab550f-6242-45eb-ac3d-3c1519340555"
/dev/nvme0n1p4: UUID="CDD5-5655" TYPE="vfat" PARTLABEL="EFI" PARTUUID="35a960a5-317c-4488-bb2d-70914d4f0256"
/dev/sdc: UUID="33d48f90-1c58-12ad-0eb0-240f7a054b2f" UUID_SUB="a9a3925d-c3c7-c296-fb35-19c3a6d2365b" LABEL="ubuntu-nvr:0" TYPE="linux_raid_member"
/dev/sdd: UUID="33d48f90-1c58-12ad-0eb0-240f7a054b2f" UUID_SUB="874fd9ca-9953-f7d3-355f-f24b61bf6790" LABEL="ubuntu-nvr:0" TYPE="linux_raid_member"
/dev/nvme0n1: PTUUID="a1cf6f96-03db-4698-870b-6094a6196506" PTTYPE="gpt"

```
```
root@ubuntu-nvr:/home/clarknova# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p1 during installation
UUID=0265d652-3271-454e-a615-735969e4d8da /               ext4    noatime,errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p4 during installation
UUID=CDD5-5655  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/nvme0n1p3 during installation
UUID=29a54ab1-32c1-40db-9196-13c223b7150f none            swap    sw              0       0
UUID=2c5b6825-3b76-4fb6-bfa4-d8a533c7734d       /unifi  xfs     noatime,nodev,noexec,logdev=/dev/nvme0n1p2      0       0
none /tmp       tmpfs noatime,mode=1777,nosuid 0 0
none /var/tmp   tmpfs noatime,mode=1777,nosuid 0 0

```
```
root@ubuntu-nvr:/home/clarknova# mount /unifi
mount: can't find UUID=2c5b6825-3b76-4fb6-bfa4-d8a533c7734d

```

---

### Post by clarknova on 2018-11-13
A couple more pieces of relevant info.

There appears to be some ambiquity as to which devices are RAID members. As noted in my original post, blkid indicates that /dev/sdc and /dev/sdd are RAID members, but the contents of /proc/mdstat appear to suggest that it's looking for /dev/sda and /dev/sdb:

```

root@ubuntu-nvr:/home/clarknova# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sda[0] sdb[1]
      7813774336 blocks super 1.2 512k chunks

unused devices: <none>

```

I tried to check dmesg for device messages, but all that's in there is a lot of this:

```

[187854.787773] XFS (md0): xfs_log_force: error -5 returned.
[187884.867493] XFS (md0): xfs_log_force: error -5 returned.
[187914.947291] XFS (md0): xfs_log_force: error -5 returned.

```

What would cause these two devices to change after boot, and what is the remedy? I don't remember how I created the md0 device. Is there a way to bring up the array based on something like blkid that would be more resilient to device name changes like this?

---

