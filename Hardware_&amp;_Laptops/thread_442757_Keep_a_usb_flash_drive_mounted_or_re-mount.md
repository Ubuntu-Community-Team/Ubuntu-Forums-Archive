---
title: "Keep a usb flash drive mounted or re-mount"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by ajlewis2 on 2007-05-13
When I pop the flash drive into the usb slot, it mounts just fine.  I have it set to claim a device named jump2 and to mount on /media/zip in fstab: 

/dev/jump2   /media/zip      vfat    users,exec,suid,dev,rw,auto  0  0

with a rule in 20-names.rules:

BUS=="usb", SYSFS{serial}=="09F0C17150A3992C", NAME="jump2"

I have a cronjob running a script to backup data and put the tarball on that drive.  This goes off at 4AM.  Unfortunately the drive unmounts automatically after a time and running the mount command fails, because /dev/jump2 is not a block device unless I pull the flash out and pop it back in. 

How do I get this thing to mount again without pulling it out and putting it back in?

Thanks for any clues.
Anita

---

### Post by ajlewis2 on 2007-05-16
I think I have solved it:

I moved the rule from /etc/udev/rules.d/20-names.rules to 65-persistent-storage.rules in that same directory.

I had tried it before, but I looked more carefully at that file and the rules that are persistent, have to be toward the top.  I think previously I had put it into one of the sections that causes some devices to *not* be persistent when they would otherwise be.  

I had another thought on how to make this device stay mounted if this didn't work.  I was going to try opening a terminal, probably with Ctrl-Alt-F3, and login and change directory to the mounted flash. I figured that this would keep the drive from being unmounted.  But the persistent storage seems to be the udev way of handling this.

Anita

---

