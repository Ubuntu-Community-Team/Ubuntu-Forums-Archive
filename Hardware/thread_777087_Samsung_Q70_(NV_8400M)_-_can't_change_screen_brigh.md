---
title: "Samsung Q70 (NV 8400M) - can't change screen brightness"
date: 2008-05-01
forum: Hardware
---

### Post by Wildy75 on 2008-05-01
This thread is related to a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/216221") when I can't change the brightness on my Q70 with the NVidia 8400M video card. The problem seems to lie in the way the kernel module video.ko handles backlight controls on newer cards. The video module gives me a kernel bug() when I try to insert it. Here is the details:

```
yug@cheetah:~$ uname -a
Linux cheetah 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

[  129.875027] ACPI Error (utglobal-0126): Unknown exception code: 0xFFFFFFFE [20070126]
[  129.875043] Pid: 7420, comm: modprobe Tainted: P        2.6.24-16-generic #1
[  129.875060]  [<c024b714>] acpi_format_exception+0x35/0x3f
[  129.875079]  [<c024a516>] acpi_ut_exception+0xc/0x55
[  129.875093]  [<f8d8b9e4>] acpi_video_bus_add+0xb0b/0xb1a [video]
[  129.875110]  [<c01d2a5d>] sysfs_addrm_start+0x6d/0xb0
[  129.875125]  [<c01d37a3>] sysfs_create_link+0x93/0x110
[  129.875144]  [<c024ebaf>] acpi_device_probe+0x33/0x7c
[  129.875156]  [<c027d988>] driver_probe_device+0x88/0x190
[  129.875164]  [<c02113f0>] kobject_uevent_env+0xf0/0x3d0
[  129.875180]  [<c027dbfe>] __driver_attach+0x9e/0xa0
[  129.875190]  [<c027cdbb>] bus_for_each_dev+0x3b/0x60
[  129.875205]  [<c027d806>] driver_attach+0x16/0x20
[  129.875212]  [<c027db60>] __driver_attach+0x0/0xa0
[  129.875219]  [<c027d13a>] bus_add_driver+0x8a/0x1e0
[  129.875234]  [<f8d3402f>] acpi_video_init+0x2f/0x4d [video]
[  129.875243]  [<c01506b6>] sys_init_module+0x126/0x19c0
[  129.875300]  [<c024eeb6>] acpi_bus_register_driver+0x0/0x38
[  129.875325]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  129.875351]  =======================
[  129.875355] ACPI Exception (video-1718): UNKNOWN_STATUS_CODE, Cant attach device [20070126]
[  129.875855] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input10
[  129.920519] ACPI: Video Device [NVID] (multi-head: yes  rom: no  post: no)
[  129.921011] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input11
[  129.973472] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

```

Any thoughts on this one? This bug on Launchpad seems just not so popular...

---

### Post by temcat on 2008-05-30
Bump! I have the same problem, really need it solved too :-(

---

### Post by Wildy75 on 2008-06-07
> **temcat said:**
> Bump! I have the same problem, really need it solved too :-(

OK, so there is a [supposed] regression from the previous kernel version.
There were reports of the backlight beginning to work properly on the BIOS version older than 10ST. But I haven't personally tried that, have the 15ST, and the backlight will only change at boot.

Hm... maybe I should've tried compiling the latest and greatest official kernel from kernel.org? Will try that ASAP (where P is boolean and S is undetermined yet =^_^=)

---

