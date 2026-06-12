---
title: "WD USB Hard Drive Not Detected on Boot"
date: 2015-05-25
forum: Hardware
---

### Post by daniel160 on 2015-05-25
Hello all,
I recently installed Kubuntu and its working great. I have a pure linux system, no dual boot. Here are my specs:

CPU: Intel 5820K
Mother Board: ASUS X99 Sabretooth
Video Card: Geforce GTX 970 Mini
RAM: 16GB Corsair Vengeance 
Liquid Cooled

I am trying to mount a WD My Book Essential USB HD at boot time. For some reason, it is not recognized at boot time which is presumably why is doesn't mount. The usb_storage module is enabled. If I unplug the drive and plug it in after I am in KDE then it mounts just fine so I know the drive is working.

Here is my fstab line for the USB drive:
```

 [FONT=monospace][COLOR=#000000]UUID=C6B89CABB89C9B8D   /media/usbda    ntfs-3g defaults,nobootwait,nofail,uid=900,gid=900,users,locale=en_US.UTF-8     0       0[/COLOR]
[/FONT]

```

It's an NTFS partition that I mount as a specific non-root user so I can do a Samba share that anyone can access. Also, I installed Kubuntu in UEFI mode and the USB Drive is on a USB 3.0 port since it supports USB 3.0.

---

### Post by weatherman2 on 2015-05-25
Are you sure the directory /media/usbda already exists?  When you manually mount a partition with Nautilus, it creates a directory for you (and when you unmount, it removes that directory), but when you mount a partition in fstab, the directory must exist already.

I prefer not to mount partitions in /media when I put them in fstab - I leave /media for the partitions I'd mount with Nautilus.  Personally, I'd use the /mnt directory - create subdirectories there that I'll use for mounting partitions in fstab.

---

### Post by daniel160 on 2015-05-25
> **weatherman2 said:**
> Are you sure the directory /media/usbda already exists?  When you manually mount a partition with Nautilus, it creates a directory for you (and when you unmount, it removes that directory), but when you mount a partition in fstab, the directory must exist already.

I prefer not to mount partitions in /media when I put them in fstab - I leave /media for the partitions I'd mount with Nautilus.  Personally, I'd use the /mnt directory - create subdirectories there that I'll use for mounting partitions in fstab.

Yes, the directory is there. I will use mnt for neatness sake. Still though, if I do a lsusb I do not see the WD drive just after boot. If I unplug and replug it back in then do lsusb I see the WD drive.

---

