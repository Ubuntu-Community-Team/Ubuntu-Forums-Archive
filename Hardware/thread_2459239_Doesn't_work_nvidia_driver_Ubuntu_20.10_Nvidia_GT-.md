---
title: "Doesn't work nvidia driver Ubuntu 20.10 Nvidia GT-735M laptop HELP!!!!"
date: 2021-03-14
forum: Hardware
---

### Post by sebastian1978 on 2021-03-14
HI All!

I have SONY VAIO laptop with Nvidia GT-735M card with prime and Ubuntu 20.10.
Can't use my Nvidia card.
Tried different versions of driver from 390 to 450. When I used 390 dmesg told 'NVRM: API mismatch... kernel module 450..' so I had to install 450. After that I 'sudo prime-select nvidia'.
Still have i915 enabled:

```
lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation 3rd Gen Core processor Graphics Controller [104d:90b7]
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at d1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Sony Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [104d:90b7]

```

---

### Post by CelticWarrior on 2021-03-14
You have hybrid Intel + Nvidia graphics therefore you need both Intel and Nvidia drivers.
Intel graphics drivers are open-source, automatically installed and in use.
Nvidia graphics drivers are proprietary and only in the newer Ubuntu release they can be automatically installed if users select that option during Ubuntu installation (did you?).

So we know:
1- i915 is correct and needed for the iGPU Intel.
2 - the way to toggler graphics is typically by using the Nvidia X Server Settings and select the intended profile and reboot: "High Performance" will enable Nvidia.
3 - Proper Nvidia drivers are required for #2 to work. The alternative open-source drivers for Nvidia doesn't work in this case.

How did you installed Nvidia drivers in the first place, i.e., before trying to change versions (which is where you main problem starts)?

---

