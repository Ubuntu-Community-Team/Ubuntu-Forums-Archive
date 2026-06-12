---
title: "Fan not working in 12.04"
date: 2012-10-21
forum: Hardware
---

### Post by nowave7 on 2012-10-21
Hey all,

I've recently done an upgrade from 10.04 to 12.04.1. Among other problems, I'm also experiencing high CPU temperatures, which I thought could be fixed by running fancontrol, but I'm not able to configure it, since pwmconfig is giving me this error:

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

sensors output:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +76.0°C  (crit = +99.0°C)
temp2:        +68.0°C  (crit = +126.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +76.0°C  (high = +70.0°C)

```

I've also tried a solution proposed here [http://askubuntu.com/questions/149992/fan-on-acer-5315-not-working](http://askubuntu.com/questions/149992/fan-on-acer-5315-not-working), but this is not working for me, since sudo modprobe coretemp returns this:

```
FATAL: Error inserting coretemp (/lib/modules/3.2.0-32-generic/kernel/drivers/hwmon/coretemp.ko): No such device
```

The computer in question is Acer Aspire 5536G, and in 10.04 everything was working normally.

lspci output:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

Any ideas? Thank you in advance.

---

