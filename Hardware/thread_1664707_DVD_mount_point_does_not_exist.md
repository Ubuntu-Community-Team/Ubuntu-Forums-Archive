---
title: "DVD mount point does not exist"
date: 2011-01-11
forum: Hardware
---

### Post by sujaysraj on 2011-01-11
hi guys. absolute beginner here. i did a clean install of ubuntu 10.10 on an existing windows 7. everything works fine exept for my dvd drive. it can play commercial cd's like ubuntu live cd but cannot play dvd movies or burnt data discs. i took a look at the fstab file. this is what i saw

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f65391fc-bc14-4fbd-868a-1fad1ed2f6e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=25ff4672-b78c-479e-bbf9-94f0ba8c94d6 none            swap    sw              0       0


There is no mounting point defined for the dvd drive. i even tried adding bits to the fstab like the following

/dev/hdc /mnt/dvd auto user,noauto,exec,utf8 0 0

but it has no effect. what might be wrong with this. please help.

---

