---
title: "Cannot view second or third hard drive after distro upgrade."
date: 2014-04-29
forum: Hardware
---

### Post by matthew31 on 2014-04-29
When I open up gparted it shows both drives as available with their proper names.

However I can't seem to access either of them as it says "drive not found" for drive A and for drive B it says I don't have permission.

How can I gain access to my files again?

It says they're mounted at /dev/sdb and /dev/sdc but I can't actually get access and I do have permissions to do so.

Edit: It looks like flash drives don't work either. Something is wrong with disk mounting.

---

### Post by oldfred on 2014-04-30
You have to mount the partitions, which Nautilus will do when you click on a partition, not a drive.
And you have to give yourself ownership - chown & permissions - chmod to use that. 

If permanent drives, you may want to use fstab to have them always mounted in the same place. But if external they may not be ready during boot.

       [URL="https://help.ubuntu.com/community/FilePermissions"]https://help.ubuntu.com/community/FilePermissions

[/URL]
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab

      [/URL]
 
#if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
echo $USER 
That shows that $USER is just yourname.

     [URL="http://ubuntuforums.org/showthread.php?t=1983336"]

http://ubuntuforums.org/showthread.php?t=1983336[/URL]
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

[URL="https://help.ubuntu.com/community/FilePermissions"]
[/URL]

---

