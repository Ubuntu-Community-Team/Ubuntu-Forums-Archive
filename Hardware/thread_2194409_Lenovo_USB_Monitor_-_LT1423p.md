---
title: "Lenovo USB Monitor - LT1423p"
date: 2013-12-18
forum: Hardware
---

### Post by redredrooster on 2013-12-18
Morning all,

I have recently aquired a USB Lenovo monitor, LT1423p but it is not working in Ubuntu 13.10.  

I have read through the forums and googled like a madman and can find alot of information about displylink but nothing has helped so far.

I have looked through [this fix]("http://jochen.kirstaetter.name/blog/linux/using-aoc-usb-monitor-in-ubuntu-1304-displaylink-e1649fwu.html") but have not had any luck.

The screen goes straight into powersave mode after being plugged in, so no signal from OS.

The monitor is seen with lsusb:

```

Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 005: ID 090c:3261 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
**Bus 002 Device 006: ID 17e9:4322 DisplayLink**
Bus 002 Device 003: ID 0451:8043 Texas Instruments, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

This is from dmesg:

```

[    5.558512] usb 2-1.1.2: new high-speed USB device number 6 using ehci-pci
[    5.659538] usb 2-1.1.2: New USB device found, idVendor=17e9, idProduct=4322
[    5.659545] usb 2-1.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.659550] usb 2-1.1.2: Product: Lenovo USB Monitor
[    5.659554] usb 2-1.1.2: Manufacturer: DisplayLink
[    5.659557] usb 2-1.1.2: SerialNumber: 1S60A3UAT2EUVN244148

```

The next line in dmesg is for eth0

This is from the /var/log/syslog file:

```

Dec 18 13:13:16 project kernel: [    3.123019] usb 2-1.1.4: New USB device found, idVendor=090c, idProduct=3261
Dec 18 13:13:16 project kernel: [    3.123025] usb 2-1.1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 18 13:13:16 project kernel: [    3.123029] usb 2-1.1.4: Product: LT1423p
Dec 18 13:13:16 project kernel: [    3.123032] usb 2-1.1.4: Manufacturer: Lenovo Corporation
Dec 18 13:13:16 project kernel: [    3.123035] usb 2-1.1.4: SerialNumber: AA00000000008208
Dec 18 13:13:16 project kernel: [    3.151905] fbcon: inteldrmfb (fb0) is primary device
Dec 18 13:13:16 project kernel: [    3.356899] Console: switching to colour frame buffer device 240x67
Dec 18 13:13:16 project kernel: [    3.364591] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Dec 18 13:13:16 project kernel: [    3.364594] i915 0000:00:02.0: registered panic notifier
Dec 18 13:13:16 project kernel: [    3.385937] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 18 13:13:16 project kernel: [    3.386248] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input2
Dec 18 13:13:16 project kernel: [    3.388397] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 18 13:13:16 project kernel: [    3.388770] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
Dec 18 13:13:16 project kernel: [    3.438105] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Dec 18 13:13:16 project kernel: [    3.438374] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3

```

Any advice on how to get this screen working will be greatly appreciated, if you need more log info just let me know.

---

### Post by redredrooster on 2013-12-19
bump

---

### Post by redredrooster on 2013-12-20
If I can gt some help on this it would be really good.  I have no idea what to do from here and I really need this screen to run.

Thanks

---

### Post by redredrooster on 2014-01-08
bump

---

### Post by redredrooster on 2014-01-13
bump, if anyone has any experince with external usb displays I would really appreciate the help.  If you need more information to be able to help I will be happy to supply it.

---

