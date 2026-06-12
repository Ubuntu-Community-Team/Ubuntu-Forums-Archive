---
title: "dkms stuck while installing or removing nvidia module"
date: 2016-05-09
forum: Hardware
---

### Post by 9600xt on 2016-05-09
Hi I was trying to install Nvidia 364.19 driver from [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) on Ubuntu 16.04 on my laptop msi-ge60 2pe with a gtx 860m, but installation will stuck at:
```
Loading new nvidia-364-364.19 DKMS files...First Installation: checking all kernels...
Building only for 4.6.0-040600rc7-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600rc7-generic

```
the same with all other kenel on my system 4.4.0 too, now i can't install or remove anything because always i receive the message "E: dpkg was interrupted you need to execute the command "sudo dpkg --configure -a"  to correct the problem", but doing this command will stuck again at the same point....


EDIT:
I solved myself doing:
```
[COLOR=#111111][FONT=Consolas]sudo dpkg --remove --force-remove-reinstreq nvidia-364[/FONT][/COLOR]
```

---

