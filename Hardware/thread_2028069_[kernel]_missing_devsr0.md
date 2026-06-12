---
title: "[kernel] missing /dev/sr0"
date: 2012-07-17
forum: Hardware
---

### Post by lo.j on 2012-07-17
hi all.

i've recompiled my kernel (3.4.x) and i'm not able to bring the cd/dvd device up:```
$ ls /dev/{scd,sr}*
ls: cannot access /dev/scd*: No such file or directory
ls: cannot access /dev/sr*: No such file or directory
```

i'm sure that each the ide/sata controller has its own "driver in use" loaded.

this is what i have in my kernel config, concerning "dev":```
$ cat /usr/src/linux/.config | grep -P '=[ym]' | grep -i dev
CONFIG_BLK_DEV_INITRD=y
CONFIG_BLK_DEV_BSG=y
CONFIG_BLK_DEV=y
CONFIG_BLK_DEV_LOOP=y
CONFIG_BLK_DEV_SD=y
**CONFIG_BLK_DEV_SR=y**
CONFIG_BLK_DEV_MD=y
CONFIG_NETDEVICES=y
CONFIG_INPUT_MOUSEDEV=m
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_EVDEV=y
CONFIG_DEVPORT=y
CONFIG_VIDEO_DEV=m
CONFIG_V4L2_MEM2MEM_DEV=m
CONFIG_USB_VIDEO_CLASS_INPUT_EVDEV=y
CONFIG_VIDEO_MEM2MEM_TESTDEV=m
```

and i've just noticed that if i add the following it won't mount / anymore:```
CONFIG_SYSFS_DEPRECATED=y
CONFIG_SYSFS_DEPRECATED_V2=y
CONFIG_DEVTMPFS=y
CONFIG_DEVTMPFS_MOUNT=y
```

any suggestion would be greatly appreciated, thanks very much!


:: edit
i forgot to mention that everything works fine with linux-image-3.2.0-26-generic so that i'm pretty sure the problem is with the kernel configuration itself.

---

### Post by lo.j on 2012-07-18
some more infos:[LIST]
[*]dmesg does not report anything about cd/dvd/sr
[*]no success with with either CONFIG_CDROM_PKTCDVD or CONFIG_CHR_DEV_SG
[/LIST]

---

### Post by lo.j on 2012-07-21
update.

i've just tried the following (all together) with no success:```
CONFIG_DEVTMPFS=y
CONFIG_DEVTMPFS_MOUNT=y
CONFIG_CDROM_PKTCDVD=y
CONFIG_CDROM_PKTCDVD_BUFFERS=8
CONFIG_BLK_DEV_SR_VENDOR=y
CONFIG_CHR_DEV_SG=y
```

---

### Post by lo.j on 2012-07-22
if anyone would ever read it, this is my full .config...

---

### Post by lo.j on 2012-07-25
up.

---

### Post by lo.j on 2012-07-26
ok, my fault...

the dvd-rom is pata! ](*,)

---

