---
title: "HD in fstab won't mount at boot"
date: 2009-01-24
forum: Hardware
---

### Post by wwarren on 2009-01-24
I have two external USB hard drives with data that I want mounted when the system boots.  I'm having a problem where one of them won't mount reliably when the system boots.  The two relevant lines from fstab read:
```
LABEL=antec  /mnt/antec  ext3  user,suid,dev,exec  0  0
LABEL=mybook /mnt/mybook  ext3  user,suid,dev,exec  0  0
```

The "antec" drive mounts automatically every time.  The "mybook" never mounts at boot.  However, once booted, "sudo mount /mnt/mybook" will successfully mount it.  If I remove the "mybook" line from fstab, it will reliably automount to /media/mybook and appears on the desktop.  When that happens, there's no corresponding line in fstab, but mtab has a line reading ```
/dev/sdc1 /media/mybook ext3 rw,nosuid,nodev,uhelper=hal 0 0
```
Any suggestion of what the problem might be is appreciated.

Ubuntu 8.10 desktop
Drive "antec" is a Western Digital 1TB WD10EAC drive in an external USB enclosure
Drive "mybook" is a Western Digital 1TB Mybook external USB drive which uses an identical WD10EAC drive.

Update:  Solved, but I don't know why.  I swapped the USB ports each HD was plugged into and they're both mounting fine so far.

wwarren

---

