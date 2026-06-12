---
title: "Permissions lost after resize partitions in Lucid fresh install"
date: 2010-05-23
forum: Hardware
---

### Post by eaglemystic69 on 2010-05-23
Did a fresh install of Lucid, then resized the partitions (should of been done 1st in gparted) though now my custom apps and time are invested. . .

Now have "denied permissions" with my internal partition and with my external HD.  I can use Nautilus to move things around, though now need to work with Avidemux and cannot open the file one partition away.


I have:
updated permission properties main folders
Gone into user/groups in admin and checked all appropriate boxes.
And spent some time looking over threads, yet Im not great with terminal work.


Here is some info that is usually asked:
eagle@eagles-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b23a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2040    16385276   83  Linux
/dev/sda2           37469       38914    11603969    5  Extended
/dev/sda3            3571       37468   272285685   83  Linux
/dev/sda4            2041        3570    12289725   83  Linux
/dev/sda5           37469       38914    11603968   82  Linux swap / Solaris

Partition table entries are not in disk order
eagle@eagles-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d6a38fbb-c5eb-4663-9804-d42706937037 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
eagle@eagles-laptop:~$ sudo blkid
/dev/sda1: UUID="d6a38fbb-c5eb-4663-9804-d42706937037" TYPE="ext4" 
/dev/sda3: LABEL="Documents" UUID="2285e844-648d-49a1-b59f-5971e4877b29" TYPE="ext4" 
/dev/sda5: UUID="99640236-98ca-4ec1-b55e-458a2715d085" TYPE="swap"

---

