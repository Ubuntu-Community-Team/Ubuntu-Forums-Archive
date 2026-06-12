---
title: "USB-C doesn't work"
date: 2020-11-04
forum: Hardware
---

### Post by holysword on 2020-11-04
As the title says, USB-C doesn't work in my laptop:
 - Ubuntu 20.04
- GPU: Nvidia RTX2060 
- nvidia-drivers-450.80.02

Dmesg -w shows no activity upon plugging or unplugging anything on the USB-C port. I've tried different cables, which work on other computers (windows machines). Surprisingly, it does detect the port and has a driver for it. The output of `lspci | grep -i usb` is:
```
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)

```
and the verbose output of the Type-C UCSI Controller is:
```

01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
        Subsystem: NVIDIA Corporation TU106 USB Type-C UCSI Controller
        Flags: bus master, fast devsel, latency 0, IRQ 128
        Memory at b4004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Power Management version 3
        Capabilities: [100] Advanced Error Reporting
        Kernel driver in use: nvidia-gpu
        Kernel modules: i2c_nvidia_gpu

```

I'd appreciate suggestions.

---

