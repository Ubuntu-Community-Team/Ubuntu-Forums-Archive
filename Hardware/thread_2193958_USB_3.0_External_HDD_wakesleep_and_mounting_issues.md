---
title: "USB 3.0 External HDD wake/sleep and mounting issues"
date: 2013-12-15
forum: Hardware
---

### Post by arcooke on 2013-12-15
I have a multi-part issue here.  My HTPC (Intel NUC d54250wyk) is running 12.10, kernel 3.10.24-031024-generic.  I have a USB 3.0 external hard drive attached for my media storage. 

**Problem #1**:  The hard drive falls asleep after about 5 minutes of inactivity.  Then, for no apparent reason, after about 5 minutes it wakes itself back up.  I'm not sure what's causing it to wake up or how to stop it

**Problem #2**:  Something about this wake/sleep cycle is screwing up my mount points.  I have it set up in fstab to mount /dev/sdb1 to /media/Storage.  On boot, this is what happens.. so that's good.  BUT .. if the drive falls asleep and gets woken up, suddenly it gets mounted to /media/<user>/Storage ... this is causing issues with XBMC being unable to find my media.

I don't care if the drive stays awake 24/7 or sleeps until access is requested (that is preferred, since I don't use it too often). 

fstab:
```
/dev/sdb1       /media/Storage  ntfs-3g defaults,locale=en_US.utf8      0       0
```


Any ideas?

---

### Post by pazbom on 2013-12-16
I am also having USB related problems with a USB-3 RAID hard drive in 12.04.3 LTS - kenel 3.5.0-32-generic.
I have a USB external hard drive and all was fine until a few month's ago when I started getting USB disconnect a few minutes after plugging the device or rebooting the system (usb 1-7: USB disconnect, device number 18)
From my investigation so far the problem seem to have started 31 October 2013 and now I believe since a specific update:
Start-Date: 2013-10-30  23:33:59
Commandline: aptdaemon role='role-commit-packages' sender=':1.21820'
Upgrade: upower:i386 (0.9.15-3git1, 0.9.15-3git1ubuntu0.1), libdecoration0:i386 (0.9.7.12-0ubuntu2, 0.9.7.12-0ubuntu3), libupower-glib1:i386 (0.9.15-3git1, 0.9.15-3git1ubuntu0.1), fire
fox-globalmenu:i386 (24.0+build1-0ubuntu0.12.04.1, 25.0+build3-0ubuntu0.12.04.1), compiz-plugins-default:i386 (0.9.7.12-0ubuntu2, 0.9.7.12-0ubuntu3), firefox:i386 (24.0+build1-0ubuntu0
.12.04.1, 25.0+build3-0ubuntu0.12.04.1), gir1.2-upowerglib-1.0:i386 (0.9.15-3git1, 0.9.15-3git1ubuntu0.1), firefox-locale-en:i386 (24.0+build1-0ubuntu0.12.04.1, 25.0+build3-0ubuntu0.12
.04.1), firefox-locale-pt:i386 (24.0+build1-0ubuntu0.12.04.1, 25.0+build3-0ubuntu0.12.04.1), compiz:i386 (0.9.7.12-0ubuntu2, 0.9.7.12-0ubuntu3), compiz-core:i386 (0.9.7.12-0ubuntu2, 0.
9.7.12-0ubuntu3), compiz-gnome:i386 (0.9.7.12-0ubuntu2, 0.9.7.12-0ubuntu3)
End-Date: 2013-10-30  23:34:11
Probably "upower" related?

---

