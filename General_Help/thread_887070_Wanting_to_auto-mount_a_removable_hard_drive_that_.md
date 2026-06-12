---
title: "Wanting to auto-mount a removable hard drive that changes its dev entry"
date: 2008-08-11
forum: General Help
---

### Post by Zeroangel on 2008-08-11
Hi, i'm trying to automatically have a removable hard drive mounted on boot via BASH. The problem here is that sometimes the removable HD changes its device name, sometimes its sdb3, sometimes its sdc3, etc. The 'name' of the partition on the removable hard drive is 'Vanguard' so if I can find a way to mount it by the partition name, it would be much easier. The mount command I use right now is:

mount -t ntfs -o rw,users,umask=0000,uid=1000,gid=100 /dev/sdb3 /media/Vanguard

Can anyone tell me what command or bash script I would have to use to mount it without having to refer directly to its device name?

---

### Post by loboc on 2008-08-11
IF HAL is working properly it will mount it itself to the same spot all the time based on volume name

change the drive label name in windows to Vanguard and let ubuntu automount it. delete /media/Vanguard and it will mount to /media/Vanguard by itself

---

### Post by loboc on 2008-08-11
[http://discoverlinux.blogspot.com/2008/06/concept-of-volume-label-in-linux.html](http://discoverlinux.blogspot.com/2008/06/concept-of-volume-label-in-linux.html)

Here is a generic explanation

---

### Post by loboc on 2008-08-11
> **loboc said:**
> [http://discoverlinux.blogspot.com/2008/06/concept-of-volume-label-in-linux.html](http://discoverlinux.blogspot.com/2008/06/concept-of-volume-label-in-linux.html)

Here is a generic explanation

Heres the ubuntu Howto

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Fixman on 2008-08-11
You may just run
```
 sudo mount -a 
```
To mount all partitions, including that one (if its on fstab).

---

### Post by Zeroangel on 2008-08-12
BRILLIANT! :KS

This worked like a charm, and it was so easy to do. Since I already had a volume label on the partition. I edited my fstab to say:
```
LABEL=Vanguard /media/Vanguard ntfs defaults 0 0
```Now the drive has its files accessible immediately at startup, and with write/execute permissions. This is exactly what I wanted to do. Thanks again. :)

---

