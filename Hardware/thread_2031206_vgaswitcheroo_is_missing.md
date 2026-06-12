---
title: "vgaswitcheroo is missing"
date: 2012-07-21
forum: Hardware
---

### Post by Becks21 on 2012-07-21
Hi there,

just installed ubuntu 12.04 x64 on a ivy-brigde laptop with dedicated ati 7970m.

My problem is, that "vgaswitcheroo" is missing and I am unable to deactivate the discrete GPU.

I mount debugfs on boot.
No propriatery drivers for the ati/intel graphics are installed.

```
root@lapbecksubuntu:/home/michael# lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 6800

```

The kernel reports to be compiled with vgaswitcheroo:
```
root@lapbecksubuntu:/home/michael# grep -i switcheroo /boot/config-3.*
/boot/config-3.2.0-23-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.2.0-26-generic:CONFIG_VGA_SWITCHEROO=y

```

Whats wrong?

Help is very appreciated.

---

