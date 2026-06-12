---
title: "Unable to mount 2 USB Hard Disk!!!!"
date: 2011-01-18
forum: Hardware
---

### Post by PenguinOfSteel on 2011-01-18
Hi to all!!!

I have googled for this problem but without finding any solution...

I have an USB disk (self-powered) plugged and recognized correctly by the system... If I connect a second USB HD (this is powered externally, not through the USB) the first one disappear and I am unable to mount it even if I unplug and re-plug it!

This happens both if I let the two disk to automount or if I define the mount in fstab 
```

/dev/disk/by-uuid/6853-5BA9                 /media/LACIE                        vfat  user,auto,rw,uid=rgonelladiaza,gid=100513	0	0
/dev/disk/by-uuid/4A94AEA694AE93CB          /mnt/BACKUPHD                       ntfs  umask=022,defaults,nls=utf8,uid=rgonelladiaza,gid=100513	0	0

```

The strange thing is that when I connect the second hard disk, the first one disappear from /dev/disk/by-uuid

I'm on Ubuntu Maverick 64 bit.

Thanks for help!!!!

---

### Post by PenguinOfSteel on 2011-01-28
Nobody can help?

---

