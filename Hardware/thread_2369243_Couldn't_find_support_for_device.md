---
title: "Couldn't find support for device?"
date: 2017-08-20
forum: Hardware
---

### Post by tmccaffery on 2017-08-20
I am getting this message in syslog. I don't even know what this device is. How can I find out?

Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0': not supported by any plugin

---

### Post by vocx on 2017-08-20
> **tmccaffery said:**
> I am getting this message in syslog. I don't even know what this device is. How can I find out?

Couldn't find support for device at '/sys/devices/pci0000:00/0000:**00:1c.4**/0000:04:00.0': not supported by any plugin


I think the last numbers tell you the device number in the PCI bus. So check by running "lspci".
```

lspci -nnk

```
Probably your device is number **00:1c.4**
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
    Subsystem: Lenovo Broadwell-U Integrated Graphics [17aa:5037]
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: Lenovo Broadwell-U Audio Controller [17aa:5034]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 [8086:9c9a] (rev e3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 [8086:9c94] (rev e3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
**00:1c.4 PCI bridge** [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 [8086:9c98] (rev e3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp

```

In my computer it seems to be part of the PCI-E bus. So, it's basically something internal of the motherboard, not a specific peripheral, like a keyboard or mouse.

---

### Post by tmccaffery on 2017-08-20
Thanks fixed

---

