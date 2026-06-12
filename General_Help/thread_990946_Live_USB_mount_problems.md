---
title: "Live USB mount problems"
date: 2008-11-23
forum: General Help
---

### Post by Tomdarkness on 2008-11-23
Hey,

Recently using my Live USB copy of Ubuntu I removed a USB drive and for some reason it thought it was still there and had not unmounted. Additionally I could not mount any more drives. I thought nothing of it and shutdown when I had finished.

Now when booting up it won't start X Server (Could not start the x server). Think the problem is with this error I am getting on boot:

mount: can't open /etc/mtab for writing: Stale NFS file handle

Also I can't find any file/folder called /etc/mtab and I have tried to recreate the file by commands I have found on the internet but it just complains about this Stale NFS file handle.

I am very new to Ubuntu so any help will be greatly welcomed :) 

Thanks,

Tom

---

### Post by SPr on 2008-11-23
I assume a live usb stick can save settings etc unlike a live CD.

> **Tomdarkness said:**
> Hey,

Recently using my Live USB copy of Ubuntu I removed a USB drive and for some reason it thought it was still there and had not unmounted.

Can you paste the contents of /etc/fstab and the output of ```
sudo fdisk -l
```
If you recognise the USB drive in /etc/fstab or in the result of sudo fdisk -l try unmounting the drive again. If it still wont unmount try ejecting it ```
sudo eject -s /dev/xxx
``` (xxx=the usb drive).

---

### Post by Tomdarkness on 2008-11-23
fstab:

```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

fdisk -l

```

Cannot open /dev/sda

```

Full errors that I get on startup:

```

 * Preparing restricted drivers...
mount: can't open /etc/mtab for writing: Stale NFS file handle
[fail]

```

```

* Cannot initalize /etc/mtab.
/etc/rcS.d/S22mtab.sh: 178: cannot create /etc/mtab: Stale NFS file handle
* Checking file systems..
fsck 1.41.3 (12-Oct-2008) [ OK ]
* Mounting local filesystems...
mount: can't open /etc/mtab for writing: Stale NFS file handle
[fail]
* Activating swapfile swap... [ OK ]
df: Warning: cannot read table of mounted file systems: Stale NFS file handle

```

---

### Post by Tomdarkness on 2008-11-24
Only way I have found to fix this problem is to format the partition although since this has happened more than once a more practical approach would be good.

---

### Post by SPr on 2008-11-25
From those reports I assume /dev/sda may be the culprit. Did you try to unmount /dev/sda or eject -s /dev/sda ?

---

