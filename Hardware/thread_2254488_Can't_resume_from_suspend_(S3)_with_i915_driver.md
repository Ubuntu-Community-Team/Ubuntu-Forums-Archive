---
title: "Can't resume from suspend (S3) with i915 driver"
date: 2014-11-27
forum: Hardware
---

### Post by olegon.ru on 2014-11-27
uname -a
Linux HP 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
This is my beloved wife's HP ProBook 4740s
Ubuntu is very good distr, but some problem is occured.
I disabled Radeon card (in BIOS) and using i915. All fglrx and fglrx-updates is completely removed, xorg-radeon too.
> lshw -c video
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)

Suspend by menu at right upper corner. Waits... Wake up by button. Wallpaper and logon screen is appeared, periodically I can login and begin work, but not more than 5 seconds and system completely freezed. I can stay at login screen without keypress and its freezed too.
No mouse, keyboard, led or ssh activity is allowed. Kernel died.
Using fglrx or fglrx-updates it's no problem with suspend and resume, while using discrete card. But I need integrated only. With radeon many other problems.
Looking for other ideas, how to debug or workaround this problem :(

---

### Post by olegon.ru on 2014-11-28
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1397277](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1397277)
](*,)

---

