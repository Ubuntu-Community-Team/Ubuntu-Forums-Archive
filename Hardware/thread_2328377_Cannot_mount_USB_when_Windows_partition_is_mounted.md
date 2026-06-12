---
title: "Cannot mount USB when Windows partition is mounted"
date: 2016-06-20
forum: Hardware
---

### Post by raamizh on 2016-06-20
When I use this command to mount my Windows 10 Partition <sudo mount -t ntfs-3g -o ro /dev/sda2 /media/raamiz> I am unable to then mount a USB drive, I get this error <Error creating mount point `/media/raamiz/KINGSTON': Read-only file system> , this USB can be mounted and works as normal when the Windows parition isn't mounted. I'm using Ubuntu Gnome 16.04

---

### Post by yancek on 2016-06-20
You have your windows partition mounted to the mount point "/media/raamiz" and mounted as read-only which is why you get the error message.  Create a mount point under that directory to mount the windows partition:  sudo mkdir /media/raamiz/windows as an example.  You are trying to mount to a mount point which is already mounted and mounted read-only per your command.

---

