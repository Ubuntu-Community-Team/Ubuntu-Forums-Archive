---
title: "Error &quot; kernel panic -not syncing &quot; after compiling new kernel"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by Rocafort8 on 2009-09-12
Yesterday i tryed to do my first kernel compilation, and when i try to load it i get the error:

**[   0.624435] Kernel panic - not syncing: VFS : Unable to mount root fs on unknown-block (0,0)**

The steps i followed are the next:

1-Download the kernel and place it in /usr/src/linux-headers-2.6.31/
2**-make menuconfig** and load the old configuration
3-Make
4-make modules
5-make modules_install
6-make install

So i go to the /boot/ folder and i found the new files **System.map-2.6.31**, **vmlinuz-2.6.31** and** config-2.6.31.**

I noticed that the other kernel i have already installed ( 2.6.24 ) have an **initrd.img-2.6.24-generic** file, i tryed yaird to generate it, but it throws me the following errors:

 mkinitrd.yaird -o/boot/initrd.img-2.6.31-generic 2.6.31

yaird error: unrecognised device: /sys/devices/platform/i8042/serio0/input
yaird error: unrecognised device: /sys/devices/platform/i8042/serio0/input/input1
yaird error: unrecognised device: /sys/devices/virtual
yaird error: unrecognised device: /sys/devices/virtual/input
yaird error: unrecognised device: /sys/devices/virtual/input/input5
yaird error: unrecognised device: /sys/devices/virtual
yaird error: unrecognised device: /sys/devices/virtual/input
yaird error: unrecognised device: /sys/devices/virtual/input/input6
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input
yaird error: unrecognised device: /sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
yaird error: unrecognised device: /sys/devices/virtual
yaird error: unrecognised device: /sys/devices/virtual/input
yaird error: unrecognised device: /sys/devices/virtual/input/input9
yaird error: uuid '1e70b5e1-2e16-48d3-a99f-c01c1d6d2e2e' not found (/etc/fstab:6) (fatal).

---

