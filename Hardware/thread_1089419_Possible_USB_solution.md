---
title: "Possible USB solution"
date: 2009-03-07
forum: Hardware
---

### Post by winzer on 2009-03-07
This goes out to those that have been having trouble with their usb flash drives.I had trouble with my usb getting to mount.It would not auto mount and manually mounting it wouldn't work. 
One such remedy that worked for me was editing the fstab file in /etc and adding:
```
/dev/sdb1 /mnt/usbflash ntfs-3g force 0 0
```
Now this was for my device in particular. The format being NTFS.
This will depend on your device. The file will give you the info you need. 
I am defiantly not guaranteeing this for everyone for it works perfectly for me!

---

### Post by albandy on 2009-03-07
when you need to use the force command is because you removed it from windows without selecting to remove it safely option.

---

