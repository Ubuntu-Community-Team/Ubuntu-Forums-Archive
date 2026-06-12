---
title: "Problem automounting partiton after karmic upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by foxbeard on 2009-10-30
I dualboot windows on my machines, and I set up /etc/fstab to automount windows' NTFS partitons on ubuntu's startup.
Since I upgraded from Jaunty to Karmic, I've noticed that my drive mounts, but the places menu now shows the drive twice, one of which is mounted, the other of which gives an error when selected about how an unprivileged user can't mount with fuse.
While this hasn't caused any debilitating problems yet, it is annoying.
I have the same problem on both my desktop and netbook, and I was able to easily recreate it on a VM.
Any ideas on how to fix this? I'ts been working fine since Intrepid, and I've come to depend on these NTFS drives being automounted.

here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d1a2cf52-6b7e-48cb-8795-753695132cf3 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=8c546ea0-abe6-431a-ab15-384c3e242f1b /home           ext4    relatime        0       2
# /media/ACER was on /dev/sda2 during installation
UUID=20682C9CF001C7B1 /media/ACER     ntfs-3g    defaults,users,exec,rw,locale=en_US.UTF-8 0 0
# swap was on /dev/sda7 during installation
UUID=3e056447-ce78-49ca-8794-caa6bb44196a none            swap    sw              0       0
```

-Matt

---

### Post by foxbeard on 2009-11-02
bump
-Matt

---

### Post by foxbeard on 2009-11-05
I think I managed to figure it out on my own. Figured I'd post it for anyone else with this problem. If I remove the 'users' option, it seems to fix the problem. I put that in there originally to fix a permissions problem I was having sharing dropbox's directory between ubuntu and windows (on the NTFS partiton), but I don't seem to be getting that anymore either.
-Matt

---

### Post by feign2 on 2009-11-05
Thank you Matt!! It was indeed an annoying problem as these "broken" and unmounted drives also appears in every save (& others) dialogs like a plague with identical names.

I am sure that we are not the only ones to find this annoying.

Seem this is an ongoing problem due to changes in auto mount/authorization modules:
[https://bugs.launchpad.net/ubuntu/karmic/+source/gvfs/+bug/396448](https://bugs.launchpad.net/ubuntu/karmic/+source/gvfs/+bug/396448)

The alternative is to auto-mount them to /mnt instead of /media. The side effect is that they will no longer show up in Nautilus or dialogs. The way around that is to use symlinks and bookmarks.

---

### Post by Platypus123 on 2009-11-24
Indeed thank you Matt!  Have either of you figured out how to set the drives to automount in a way that they appear in Nautilus without bookmarks?

---

