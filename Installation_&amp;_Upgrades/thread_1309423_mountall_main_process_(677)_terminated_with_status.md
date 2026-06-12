---
title: "mountall main process (677) terminated with status 127"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by mundo on 2009-11-01
Hi guys,

I attempted to upgrade from 9.04 to 9.1 but I can't boot now and just get this error message:

```
mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (677) terminated with status 127
```

Any ideas?

---

### Post by sikosis on 2009-11-03
yeh I had the same problem -- haven't been able to fix it yet. I saw one guy posted he did a reinstall, which isn't really a fix.

---

### Post by mundo on 2009-11-03
I think it will have to be a reinstall!

---

### Post by jvroutak on 2009-12-25
I had the same problem. I was trying to update 9.04 to the latest packages, but had the apt configuration wrong so the update actually installed some packages from 9.10. I could save the situation by upgrading to the 9.10 altogether (although I would have preferred to stay with the 9.04 which worked fine and 9.10 doesn't bring anything new or better, I had no  idea how I could have downgraded the upstart stuff back to the 9.04 sysvinit state and was in a hurrt). I had the same non-bootable state (which of course should never happen) because the udev, upstart, mountall and friends were not working. 

I could recover from the situatution using the 9.04 Live-CD (9.10 CD wouldn't even boot to an usable state).

In the live-CD session, start a terminal and use chroot.

```

sudo su
cd /
mount <path-to-root-partition> /mnt
#next line only if you have a separate boot partition
mount --bind <path-to-boot-partition> /mnt/boot 
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev /mnt/dev
chroot /mnt

#in the chroot session:
apt-get update
apt-get dist-upgrade
dpkg --configure -a

```

9.10 has the problems of its own: in my opinion, there are no steps forward and a few backward. Also stability is not so good, but that may be a result of this unorthodox upgrade, although the same problems are reported elsewhere.

---

### Post by dfme on 2010-07-19
Thanks jvroutak! Your post fixed the issue I had :-)

---

### Post by Langlois on 2010-10-22
Good evening,


Would it also possible to do this with a PC with a dual boot XP + 9.04 where Ubuntu doesn't start ?

Regards

---

