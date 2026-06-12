---
title: "ioremap error - possibly gma500/psb-gfx related"
date: 2011-12-02
forum: Hardware
---

### Post by wkatastrof on 2011-12-02
```
[   11.258452] ioremap error for 0x7f6bc000-0x7f6bf000, requested 0x10, got 0x0
```Hello everyone,

The above error is what I get everytime I boot into Ubuntu 11.10. Once that comes up on screen, it takes about a minute or two for boot to resume. I think it may be related to the work-arounds I had to do to get the psb-gfx drives to work. (Just google gma500 / poulsbo / psb-gfx to see what kind of nightmare it is to use the intel embedded graphics driver...) Those work arounds (and then some others I don't remember) can be found on this older thread: [ [http://ubuntuforums.org/showthread.php?t=1792777](http://ubuntuforums.org/showthread.php?t=1792777) ]

The system boots fine, its just the wait can be irritating sometimes. Just wondering if anyone had any suggestions on how to fix this error or atleast reduce the boot time. Below you'll find the results from 'dmesg' which surround the above error.

```
[   11.257320] gma500 0000:00:02.0: irq 41 for MSI/MSI-X
[   11.257359] gma500 0000:00:02.0: setting latency timer to 64
[   11.258452] ioremap error for 0x7f6bc000-0x7f6bf000, requested 0x10, got 0x0
[   11.258682] Stolen memory information
[   11.258689]        base in RAM: 0x7f800000
[   11.258696]        size: 7932K, calculated by (GTT RAM base) - (Stolen base), seems wrong
[   11.258705]       the correct size should be: 8M(dvmt mode=3)
[   11.262361] Set up 1983 stolen pages starting at 0x0007f800, GTT offset 0K

```Thanks.

---

### Post by wkatastrof on 2011-12-04
bump, please.

---

### Post by wkatastrof on 2011-12-06
bump

---

### Post by wkatastrof on 2011-12-16
bump.

---

### Post by GreatEmerald on 2012-02-14
I have a very similar problem here as well, using Fujitsu Stylistic Q550 tablet, also with psb-gfx (gma500-gfx). The memory mapping is very similar, here it's 0x7f57900-0x7f57a000. According to /proc/iomem (and the firmware), that space is "ACPI Non-volatile storage". The problem can be worked around by disabling ACPI, but of course that option is very suboptimal.

This is quite a problem, actually, because if you keep using ACPI, due to this error the gma500-gfx module crashes, and you are left with unaccelerated VESA rendering. And if you disable ACPI, the graphics module runs fine, but you lose all of the power options provided by ACPI.

My guess is that this is caused by the firmware supplying erroneous ACPI-related data that Linux uses for memory allocation, and that eventually ends with a conflict and therefore a crash. Although it could also be a bug in the kernel module itself.

I will attach the full dmesg I get during boot with no special options on the current daily xubuntu build shortly. It contains a lot of interesting ACPI-related information - perhaps someone could figure out exactly what is going on there?

EDIT: Here is the dmesg: [http://paste.ubuntu.com/842304/](http://paste.ubuntu.com/842304/)

---

### Post by bela83 on 2012-08-03
> **wkatastrof said:**
> ```
[   11.258452] ioremap error for 0x7f6bc000-0x7f6bf000, requested 0x10, got 0x0
```Hello everyone,

The above error is what I get everytime I boot into Ubuntu 11.10. Once that comes up on screen, it takes about a minute or two for boot to resume. I think it may be related to the work-arounds I had to do to get the psb-gfx drives to work. (Just google gma500 / poulsbo / psb-gfx to see what kind of nightmare it is to use the intel embedded graphics driver...) Those work arounds (and then some others I don't remember) can be found on this older thread: [ [http://ubuntuforums.org/showthread.php?t=1792777](http://ubuntuforums.org/showthread.php?t=1792777) ]

The system boots fine, its just the wait can be irritating sometimes. Just wondering if anyone had any suggestions on how to fix this error or atleast reduce the boot time. Below you'll find the results from 'dmesg' which surround the above error.

```
[   11.257320] gma500 0000:00:02.0: irq 41 for MSI/MSI-X
[   11.257359] gma500 0000:00:02.0: setting latency timer to 64
[   11.258452] ioremap error for 0x7f6bc000-0x7f6bf000, requested 0x10, got 0x0
[   11.258682] Stolen memory information
[   11.258689]        base in RAM: 0x7f800000
[   11.258696]        size: 7932K, calculated by (GTT RAM base) - (Stolen base), seems wrong
[   11.258705]       the correct size should be: 8M(dvmt mode=3)
[   11.262361] Set up 1983 stolen pages starting at 0x0007f800, GTT offset 0K

```Thanks.

Hi wkatastrof,

I have the same ioremap error on a EeePC 1101 HA. What is your hardware ?

---

