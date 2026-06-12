---
title: "ZFS CKSUM errors on UBS3 Raspberry PI 8GB model"
date: 2021-12-27
forum: Hardware
---

### Post by stafwag on 2021-12-27
Hi,


Somebody else is using ZFS on a Raspberry PI 8GB model with UBS3 successfully?



When I run a Zpool scrub I get CKSUM errors.



I tried it on 3 Raspberry Pi's, they are all the same model.



```

# dmesg | grep -i model

[    0.000000] Machine model: Raspberry Pi 4 Model B Rev 1.4

# 

```

Although an older pi 8gb (same model) seems to be fine.



Tried the same setup with a few Linux distributions (Raspberry PI os, Ubuntu, Manjaro) and they all have the same issue.



FreeBSD seems to work fine.



Tried different USB adapters, disks switched from UASP to USB storage etc. I don't see any errors with Dmesg, Syslog. 



Switching to USB2 resolves that issue.



The same setup works fine when I limit the memory to 4G ( add total_mem=4096 to config.txt) so it looks a bit similar to an old USB kernel bug (not sure if this is related to my issue)



[https://github.com/raspberrypi/linux/issues/3093](https://github.com/raspberrypi/linux/issues/3093)

---

