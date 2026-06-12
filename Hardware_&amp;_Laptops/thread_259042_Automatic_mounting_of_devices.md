---
title: "Automatic mounting of devices"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by bgedan on 2006-09-16
Hi Folks,

i've got an external usb disk, wich i'd like to mount automatically during boot-up.

Here's my aproach:

```

/etc/fstab
---------------------------------------------------------
/dev/sda5       /media/TREKSTOR    vfat  rw,user,auto 0 0
/dev/sda6       /media/TREKSTOR1   vfat  rw,user,auto 0 0

```

File permissions, directories etc are set up correctly.

Mounting the partions by running

```

mount /dev/sda5 && mount /dev/sda6

```

easily works. However the partitions aren't mounted automatically at boot-up.

The reason i'd like to have them automatically mounted is Amarok. Amarok starts with my KDE session and the disks aren't mounted at that time. If i mount them AFTER Amarok starts i have to re-scan my whole music library. That's annoying and time-wasting. (I know i could stop Amarok from auto-starting, but i find it much more comfortable to let all things be done automatically and not "click-by-click")

Any helpful comment is appreciated. Thanks in advance.

Regards
Bennet

---

### Post by bgedan on 2006-09-17
problem solved :KS

---

### Post by dabear on 2006-10-03
Hi, how did you solve your problem?

I bought a trekstor mazi z.ul when I was in Germany. Have you been able to connect the device to your router, and then mounting it over the network? How?

---

