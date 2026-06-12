---
title: "Can't get eye toy working"
date: 2009-04-15
forum: Hardware
---

### Post by Captain_Glen on 2009-04-15
Hi,

I am trying to follow this how to: [http://ubuntuforums.org/showthread.php?t=272328]("http://ubuntuforums.org/showthread.php?t=272328")

I get this error:
```
glen@glen-desktop:~$ sudo modprobe ov51x-jpeg
FATAL: Error inserting ov51x_jpeg (/lib/modules/2.6.24-19-generic/extra/ov51x-jpeg.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and when I run dmesg:
```
glen@glen-desktop:~$ dmesg | grep ov
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] Movable zone start PFN for each node
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[   37.305374] cpuidle: using governor ladder
[   37.305376] cpuidle: using governor menu
[ 3365.285962] ov51x_jpeg: disagrees about version of symbol video_devdata
[ 3365.285970] ov51x_jpeg: Unknown symbol video_devdata
[ 3365.286149] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[ 3365.286152] ov51x_jpeg: Unknown symbol video_unregister_device
[ 3365.286222] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[ 3365.286225] ov51x_jpeg: Unknown symbol video_device_alloc
[ 3365.286258] ov51x_jpeg: disagrees about version of symbol video_register_device
[ 3365.286261] ov51x_jpeg: Unknown symbol video_register_device
[ 3365.286366] ov51x_jpeg: disagrees about version of symbol video_usercopy
[ 3365.286369] ov51x_jpeg: Unknown symbol video_usercopy
[ 3365.286398] ov51x_jpeg: disagrees about version of symbol video_device_release
[ 3365.286401] ov51x_jpeg: Unknown symbol video_device_release
glen@glen-desktop:~$ 

```

---

### Post by pytheas22 on 2009-04-16
Try rebooting.  There may be module version conflicts; hopefully a reboot will resolve them.

Also, I don't see in the tutorial (in the first post, at least) where it says to modprobe ov51x-jpeg.  Are you sure you need to do that?

---

### Post by Captain_Glen on 2009-04-16
Sorry I forgot to mention I was following the instructions from their web site: [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall")

But I have it working now.  YAY! :D

I had another problem with my computer, where I couldn't install build essential.  But I fixed that and now this is fixed also.

---

### Post by Captain_Glen on 2009-04-16
God Damn it!  Sometimes I hate linux!  It has stopped working again.  My tv card had an error so I had to recompile the drivers and reboot and now my Eye Toy doesn't work.  Now I get this error:

```
glen@glen-desktop:~/Downloads/ov51x-jpeg-1.5.9$ sudo modprobe ov51x-jpeg 
FATAL: Error inserting ov51x_jpeg (/lib/modules/2.6.24-19-generic/extra/ov51x-jpeg.ko): Unknown symbol in module, or unknown parameter (see dmesg)
glen@glen-desktop:~/Downloads/ov51x-jpeg-1.5.9$ 

```

and dmesg:
```
glen@glen-desktop:~/Downloads/ov51x-jpeg-1.5.9$ dmesg |grep  ov
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] Movable zone start PFN for each node
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[   39.149805] cpuidle: using governor ladder
[   39.149806] cpuidle: using governor menu
[ 1525.386149] ov51x_jpeg: disagrees about version of symbol video_devdata
[ 1525.386156] ov51x_jpeg: Unknown symbol video_devdata
[ 1525.386346] ov51x_jpeg: disagrees about version of symbol video_unregister_device
[ 1525.386349] ov51x_jpeg: Unknown symbol video_unregister_device
[ 1525.386421] ov51x_jpeg: disagrees about version of symbol video_device_alloc
[ 1525.386424] ov51x_jpeg: Unknown symbol video_device_alloc
[ 1525.386458] ov51x_jpeg: disagrees about version of symbol video_register_device
[ 1525.386461] ov51x_jpeg: Unknown symbol video_register_device
[ 1525.386568] ov51x_jpeg: disagrees about version of symbol video_usercopy
[ 1525.386571] ov51x_jpeg: Unknown symbol video_usercopy
[ 1525.386601] ov51x_jpeg: disagrees about version of symbol video_device_release
[ 1525.386604] ov51x_jpeg: Unknown symbol video_device_release

```

Also if I go to Hardware Drivers it has two entries for my Eye Toy:
OV519 USB Camera Driver and ov51x USB Camera Driver both are disabled and Not in use.

---

### Post by pytheas22 on 2009-04-16
I would first try rebooting.  If that doesn't fix it, recompile the camera driver again using the instructions you originally followed.

---

### Post by Captain_Glen on 2009-04-29
Upgraded to Jaunty Jakalope and it works out of the box. :D

---

