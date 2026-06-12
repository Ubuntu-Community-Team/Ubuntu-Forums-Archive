---
title: "Can't boot after install"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by canistel on 2009-04-24
I just installed jaunty this morning from the live cd. My previous system was 8.10 and I had installed it on a software raid system.

My setup looks like this:
```

/dev/sda2  -  /boot
/dev/md0   -  /
/dev/md1   -  /home

```

So my boot partition is NOT in a raid array.

Before running the installer, I installed mdadm in the live cd so that I could setup my raid array(s) and use it in the installation.

I also did a "chroot" from the live cd into the new system after it was installed, and installed the mdadm tool into the new system.

Grub is installed on /dev/sda and grub will boot and I can see my new 9.04 system in the grub menu, but after selecting it, it tries to boot it but after some time fails with an error message like "/dev/md0" does not exist. All of this was working fine in 8.04 and in 8.10 so I'm assuming that the raid arrays are correct and still valid, I'm just missing a piece of the puzzle...

How do I get grub to boot my new system?

---

