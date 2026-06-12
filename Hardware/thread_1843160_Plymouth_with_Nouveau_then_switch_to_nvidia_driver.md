---
title: "Plymouth with Nouveau then switch to nvidia driver"
date: 2011-09-13
forum: Hardware
---

### Post by turjuque on 2011-09-13
Hello guys,

I'm trying to solve the plymouth bad resolution problem with nvidia closed source drivers.

I believe it's possible because it's working fine with my archlinux setup !

The trick is to boot with nouveau kms until you start the Xserver and swap drivers.

The thing is I don't really know how to acheive this on ubuntu.

How do I load nouveau at the very begining of the boot process.

I commented the blacklist lines in /etc/modprobe.d/nvidia-graphics-drivers.conf
But nouveau loads too late and my script to unload nouveau doesn't work when I put it in /etc/rc.local

This is the script that should unload nouveau and let Nvidia driver load.
```
#!/bin/bash
chvt 2
echo 0 > /sys/class/vtconsole/vtcon1/bind
rmmod nouveau
rmmod ttm
rmmod drm_kms_helper
rmmod drm
```

---

### Post by nerdy_kid on 2011-11-29
This is an interesting idea; did you ever get it to work?

---

