---
title: "Hard Drive Space"
date: 2020-08-06
forum: Hardware
---

### Post by prenger745 on 2020-08-06
Hello,

I just loaded up a fresh install 20.04 server on a 4TB disk.  When I key in: df-h, I can see my freespace but I don't see anything close to 4TB.  However, when I key in fdisk -l, I see that sda3 has that space.  Why doesn't it show on df -h?  How much free space do I actually have??

```
df-h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               3.8G     0  3.8G   0% /dev
tmpfs                              787M  1.4M  785M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  196G  6.3G  180G   4% /
tmpfs                              3.9G     0  3.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2                          976M  104M  805M  12% /boot
/dev/loop2                          55M   55M     0 100% /snap/core18/1705
/dev/loop1                          69M   69M     0 100% /snap/lxd/14804
/dev/sda1                          511M  7.8M  504M   2% /boot/efi
/dev/loop0                          28M   28M     0 100% /snap/snapd/7264
tmpfs                              787M     0  787M   0% /run/user/0
```

When I key in fdisk -l, I get the following:

```
Disk /dev/loop0: 27.9 MiB, 28405760 bytes, 55480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 68.99 MiB, 72318976 bytes, 141248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000VN000-2AH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: ECBEB957-A9B3-4290-92F4-73BC39C5BF90

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624    3147775    2097152    1G Linux filesystem
/dev/sda3  3147776 7814033407 7810885632  3.7T Linux filesystem




Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 200 GiB, 214748364800 bytes, 419430400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

---

### Post by TheFu on 2020-08-07
You selected to use LVM during the install.  That's great from a flexibility standpoint, but you'll need to learn to use LVM commands and gain a little understanding about the way different LVM objects relate to disks, partitions, and file systems.

LVM has PVs (physical volumes), VGs (Volume Groups), and LVs (Logical Volumes).  I'll try to find a diagram that clearly shows how those each relate.
Found one: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/logical_volume_manager_administration/lvm_definition](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/logical_volume_manager_administration/lvm_definition)

First of all, let's gather some LVM information. These commands are 100% safe - type just gather data.
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint

```
Run those and please post both the command AND the output wrapped in "code tags", otherwise the columns won't line up and it will be unreadable here.

There is no GUI for doing LVM management. Sorry.

[https://www.tecmint.com/extend-and-reduce-lvms-in-linux/](https://www.tecmint.com/extend-and-reduce-lvms-in-linux/) shows how to use the different commands to create PVs, VGs, LVs, and add more storage later to the VG, so more LVs can be added or resized larger.  There is some danger in using different physical disks in the same VG. A few decades ago, I lost 80% of my data spanning an LV across 3 physical disks. One disk failed.  It was before I had backup religion.  I don't span VGs across disks since then unless using RAID1 or RAID10 (which LVM supports).

---

### Post by prenger745 on 2020-08-07
Thank you for replying.  I will go look at some of that Documentation.  I must have selected that by mistake but it sounds like something I want to use in the future.  As far as my install, I needed to get it up and going so started fresh and went the old route.

---

### Post by TheFu on 2020-08-07
> **prenger745 said:**
> Thank you for replying.  I will go look at some of that Documentation.  I must have selected that by mistake but it sounds like something I want to use in the future.  As far as my install, I needed to get it up and going so started fresh and went the old route.

Too bad. Being crazy lazy and 10 seconds could have extended the existing LV to use all 3.6TB, if that was your desire. A 4TB disk becomes about 3.6T after format.

---

