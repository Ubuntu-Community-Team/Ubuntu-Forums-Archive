---
title: "After trying to recover ubuntu partition even winXp partition doesn't boot"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by dbeg on 2009-03-28
Hi

I installed ubuntu on second partition (on first is WinXp). After succesfull installation and rebooting the system there i couldn't choose beetwen WinXP and Ubuntu, system was automaticly booted from first partition.

i tried to recover ubuntu partition using this guide (i've booted ubuntu from flash drive):
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick)

but i wasn't able to get trough step 4 where I got the same error:

"Error 15: File not found" if I tried to write
find /boot/grub/stage1
or
find /grub/stage1

After that I quit trying to resolve the problem, but when I rebooted computer, even WinXP didn't boot from first partition!!

I'm sorry if this is a trivial problem, but I'm a beginner in Ubuntu.

---

### Post by ufuxlinux on 2009-03-28
I understand that your Ubuntu partition is on /dev/sda2. Boot into livecd, open up a terminal:

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda2 /mnt/ubuntu
sudo grub-install --root-directory=/mnt/ubuntu /dev/sda
```

(if your disk device's name is hda, replace sda's with hda)

---

### Post by dbeg on 2009-03-28
I get response

ubuntu@ubuntu:~$ mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/ubuntu
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 

?

---

### Post by dbeg on 2009-03-28
These are partitions of my HD:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24ff24ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60800   437176845    f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           19123       60800   334778503+   7  HPFS/NTFS
/dev/sda7           12749       18219    43945776   83  Linux
/dev/sda8           18220       19122     7253316   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)
```

I partitioned my 500GB disk when I installed Win XP into 3 partitions of 50GB and one with the rest of space. After that, I partitioned the second partition of 50GB with ubuntu partitioner into ext3 and swap. Can be this a problem, because now I have all patritions except first one (sda1) listed under extended sda2.

---

