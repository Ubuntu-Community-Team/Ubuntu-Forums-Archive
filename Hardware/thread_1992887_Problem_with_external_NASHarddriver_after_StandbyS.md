---
title: "Problem with external NAS/Harddriver after Standby/Sleep (different mountpoint)"
date: 2012-06-01
forum: Hardware
---

### Post by cybtrash on 2012-06-01
Hello,

I have an external NAS-RAID attached to my HTPC (home theater pc) via USB 3.0. It gets mounted automatically when starting the pc via fstab to /media/RAID:

```
xbmc@xbmc-pc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ca141a94-56a7-41d2-a237-27515d9bee71 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=86f2852b-eb9f-45dd-8adf-4e679c1ef3b5 none            swap    sw              0       0
UUID="3654DFEE54DFAF3D" /media/RAID     ntfs    rw,auto,user,fmask=0111,dmask=0000

```When I put xbmc into sleep/standby, the pc turns to sleep and the RAID automatically turns off after some seconds. When I restart the pc with the remote the RAID also starts after a few seconds. Then I get a message in XBMC, that it got successfully mounted. BUT it always gets mounted to /media/RAID_ . This is very bad, because XBMC looks for files in /media/RAID.


So what can I do to make the RAID reappear in /media/RAID? (/media/RAID still exists parallel to /media/RAID_ but it doesn't contain any files)

I tried something like a umount /media/RAID && rm /media/RAID script, but it always works in 80%. And I think there must be some other solution?

uname -a:
```

Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic i686)
Linux xbmc-pc 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 athlon i386 GNU/Linux
```

---

