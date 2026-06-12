---
title: "xorg.conf is moved to xorg.conf.date during booting"
date: 2016-09-18
forum: Hardware
---

### Post by culkan82 on 2016-09-18
Hi guys,

My xorg.conf is moved to xorg.conf.date almost every time I start my system and so that I end up with default setting for refresh rate.

xorg.conf:
```

[branko@ubuntu ~] ls -1 /etc/X11/xorg.conf*
/etc/X11/xorg.conf.09182016
[branko@ubuntu ~] 

```

graphical card:
```

[branko@ubuntu ~] lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

ubuntu with latests updates:
```

[branko@ubuntu ~] more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
[branko@ubuntu ~] 

```

The workaround is to set refresh rate via xrandr during startup:
```

xrandr --output VGA-0 --mode 1440x900 --rate 75

```
and this works. But how can I figure out what app/lib moved xorg.conf? Is this bug? I see the same here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1345585](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1345585)
and it is fixed.

Thanks.

EDIT:/ I have just seen, the problem actually happens during shutting down.

---

