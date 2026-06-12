---
title: "Screen brightness adjustment does not work"
date: 2023-10-30
forum: Hardware
---

### Post by dlsmua on 2023-10-30
Hello!

I have a laptop ASUS Vivobook D1603QA (with AMD).


There is no screen brightness adjustment. It is not adjustable from the keyboard (using special knobs) and there is no "slider" in the interface.
I deleted and reinstalled the drivers for the video card (AMD Radon) - nothing changes.
At the same time, if I boot from a flash drive (in live mode), everything works fine.
I read on the Internet that it is necessary to edit the config, but I don't have it as it should be.
```
$ cat /etc/default/grub | grep back
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

Additional info.
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy
```

```
$ sudo lspci -vnn | grep -A10 VGA
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne [1002:1638] (rev c6) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Cezanne [1043:12ad]
	Flags: bus master, fast devsel, latency 0, IRQ 47, IOMMU group 10
	Memory at ffe0000000 (64-bit, prefetchable) [size=256M]
	Memory at fff0000000 (64-bit, prefetchable) [size=2M]
	I/O ports at f000 [size=256]
	Memory at fce00000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [64] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/4 Maskable- 64bit+
08:41 dl#uni.dl.sm.ua[~] sudo lspci -k | grep -iA2 VGA
```

```
$ sudo lspci -k | grep -iA2 VGA
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne (rev c6)
	Subsystem: ASUSTeK Computer Inc. Cezanne
	Kernel driver in use: amdgpu
```

Please help to solve the problem.

---

### Post by dlsmua on 2023-11-01
[COLOR=#000000][FONT=&quot]It was necessary to do the opposite in the grub settings.
I tried the following:[/FONT][/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[COLOR=#000000][FONT=&quot]and everything worked as it should.[/FONT][/COLOR]

---

