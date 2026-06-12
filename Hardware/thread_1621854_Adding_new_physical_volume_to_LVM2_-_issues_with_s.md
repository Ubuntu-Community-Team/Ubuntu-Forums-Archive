---
title: "Adding new physical volume to LVM2 - issues with seeing volume"
date: 2010-11-14
forum: Hardware
---

### Post by flycast on 2010-11-14
Here is my fstab:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/server-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=b8425e9b-d771-4019-99f2-e211a9bd7818 /boot           ext2    defaults        0       2
/dev/mapper/server-home /home           ext4    defaults,usrquota,grpquota,acl        0       2
/dev/mapper/server-swap_1 none            swap    sw              0       0


I have a 1Tb disk that I want to add the the LVM. The disk has a partition of Ubuntu and a Partition of XP. If I remember right the grub had issues when I installed Ubuntu. I took the 1Tb drive out and put in an old 160Gb drive and installed Zentyal (a Ubuntu based server package) and it installed fine. Now I want to add my 1Tb drive to the logical volume since I am running out of room. My issue is:

1) I know nothing about using the logical volume manager
2) If I plug the 1Tb drive in I can't see it with either fdisk -l or gparted.

If I could add the 1Tb drive and get access to what is on that drive that would be great. If not then I will be happy with formatting and adding a blank volume to the LVM.

Advice? Help?

---

