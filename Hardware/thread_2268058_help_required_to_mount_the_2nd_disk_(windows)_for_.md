---
title: "help required to mount the 2nd disk (windows) for different users"
date: 2015-03-05
forum: Hardware
---

### Post by jaivenkit on 2015-03-05
Hi,

I have installed Kubuntu 14.04 LTS and created two user accounts: One for me (username: jack) and another one for my kids (username: jill)


The machine has 2 physical disks

Disk 1 has 2 partitions: 1 for windows 7 & another 1 for Kubuntu.

Disk 2 has only one partition: ntfs

Both Disk1 and Disk2 has to be mounted automatically for both the users and also I want to give only read permission to my kids account (username: jill) for all partitions.

_______________________________________________________________-
the entries in fstab is as follows:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=18c7884c-a33a-497d-892c-12978cc3e891 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d58e24ca-6936-45a0-9d87-75e42d66b150 none            swap    sw              0  
____________________________________________________________________________

Could somebody help me on this?

Thanks in advance.

---

### Post by yancek on 2015-03-05
You need to first ascertain the partitions for your windows.  Open a terminal and run the command:  sudo fdisk -l(Lower Case Letter L in the command.  Below is an entry for a windows partition with /dev/sda1 as the partition.  You can tell a windows partition by the NTFS under System.

>   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT

Once you have determined the partition device for each windows partition, you need to create a mount point.  An example would be:

```
sudo mkdir /mnt/sda1
```

Create these mount points, directories or folders for all three partitions.  Once you have done that, you can put an entry in fstab similar to the one below which should give root all permissions and users/others read only.

> /dev/sda2 /mnt/win_7 ntfs-3g auto,user,rw,umask=022 0 0

You don't need to name the mount points sda1, sda2, etc.  You can give them any name you want but need to have the same name in the fstab file.  If you want to give yourself rw permissions as a user rather than using sudo, you will need to do that with the chmod command.

Bear in mind that this will have no impact on what any user can do when booted into windows.  You will need to go to Disk Management to set permissions in windows.

---

