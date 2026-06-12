---
title: "How do I automount external firewire ntfs drive?"
date: 2008-11-01
forum: Hardware
---

### Post by ytsestef on 2008-11-01
The disk is WD My Book 1TB.

I tried ntfs-config but it doesn't show the drive, no matter whether it is already mounted or not. When I click on the drive, it mounts perfectly, with r/w access and stuff. 

I tried running the command "mount" in a terminal to see its mount options. It uses some "fuseblk" filesystem type. When I insert the line in /etc/fstab it fails to mount upon startup and it even fails to mount manually (by clicking on the drive) until I comment out the line.

This is VERY frustrating.

---

### Post by ytsestef on 2008-11-03
sorry to bump my own thread. any ideas??? i really need to automount the drive...

---

