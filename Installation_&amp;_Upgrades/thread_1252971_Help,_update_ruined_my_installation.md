---
title: "Help, update ruined my installation"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by ravalox on 2009-08-29
I was attempting an update when it seemed to stop mid installation.  It didn't freeze mind you, the installation of the updates just halted.  So I rebooted, and now I get a kernel panic.  Is there a way to salvage this or am I looking at a completely new install?

---

### Post by stlsaint on 2009-08-29
can u boot into recovery mode? try fixing broken packages option from there!

---

### Post by Gen2ly on 2009-08-29
Looks like the update got caught in a bad spot.  Best thing to do here is to chroot to your hard drive from a livecd.

You'll need to get to a terminal and mount your root partition:

```
mount /dev/<your-drive-or-partition> /mnt
```

```
su -
cd /mnt
```

```
cp /etc/resolv.conf /mnt/etc/resolv.conf
mount -t proc none /mnt/proc
mount -t sysfs none /mnt/sys
mount -o bind /dev /mnt/dev
chroot /mnt /bin/bash
source /etc/profile
```

This will put you in the your Ubuntu installed environment (for most technical reasons).  Then you can finish your upgrade:

```
apt-get upgrade
```

I don't foresee any problems with this unless something really bad happened on the upgrade.  It is a bit technical and some people are thrown off by the command line.  If your install is new and it does, might just want to re-install.

---

