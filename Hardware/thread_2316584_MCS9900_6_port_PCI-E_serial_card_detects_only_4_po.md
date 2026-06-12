---
title: "MCS9900 6 port PCI-E serial card detects only 4 ports"
date: 2016-03-09
forum: Hardware
---

### Post by hc-koch on 2016-03-09
Hey all!

I have a problem with a 6 slot serial PCI-E card Art No. 89347 ([http://www.delock.de/produkte/F_323_Seriell_89347/merkmale.html](http://www.delock.de/produkte/F_323_Seriell_89347/merkmale.html)) with chip MCS9900. Under my Linux operating system Ubuntu 14.04.3 64bit Kernel 3.19 only 4 of the 6 ports are correctly recognized apparently. My motherboard already has an onboard port, which also works.
Enclosed you will find the output of lspci -v, where 4 of the ports are apparently recognized correctly and the serial driver loaded while the other two aren't.
Furthermore, you can find a copy of the file /var/lib/setserial/autoserial.conf of the first boot after installation. Additionally my attempt to amend the configuration (unfortunately unsuccessful).
```

02:00.0 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
Subsystem: Device a000:3002
Flags: fast devsel, IRQ 16
I/O ports at e050 [disabled] [size=8]
[virtual] Memory at f7e09000 (32-bit, non-prefetchable) [size=4K]
I/O ports at e040 [size=8]
[virtual] Memory at f7e08000 (32-bit, non-prefetchable) [size=4K]
[virtual] Memory at f7e07000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
Capabilities: [78] Power Management version 3
Capabilities: [80] Express Legacy Endpoint, MSI 00
Capabilities: [100] Virtual Channel
Capabilities: [800] Advanced Error Reporting
Kernel driver in use: serial

02:00.1 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
Subsystem: Device a000:3002
Flags: fast devsel, IRQ 17
I/O ports at e030 [disabled] [size=8]
[virtual] Memory at f7e06000 (32-bit, non-prefetchable) [size=4K]
I/O ports at e020 [size=8]
[virtual] Memory at f7e05000 (32-bit, non-prefetchable) [size=4K]
[virtual] Memory at f7e04000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
Capabilities: [78] Power Management version 3
Capabilities: [80] Express Legacy Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
Kernel driver in use: serial

02:00.2 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
Subsystem: Device a000:1000
Flags: fast devsel, IRQ 18
I/O ports at e010 [disabled] [size=8]
[virtual] Memory at f7e03000 (32-bit, non-prefetchable) [size=4K]
[virtual] Memory at f7e02000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
Capabilities: [78] Power Management version 3
Capabilities: [80] Express Legacy Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting

02:00.3 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
Subsystem: Device a000:1000
Flags: fast devsel, IRQ 19
I/O ports at e000 [disabled] [size=8]
[virtual] Memory at f7e01000 (32-bit, non-prefetchable) [size=4K]
[virtual] Memory at f7e00000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
Capabilities: [78] Power Management version 3
Capabilities: [80] Express Legacy Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
```

```
###AUTOSAVE###
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
#
###AUTOSAVE###
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
/dev/ttyS4 uart 16650V2 port 0xe050 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS5 uart 16650V2 port 0xe040 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS6 uart 16650V2 port 0xe030 irq 17 baud_base 115200 spd_normal skip_test
/dev/ttyS7 uart 16650V2 port 0xe020 irq 17 baud_base 115200 spd_normal skip_test

```
```
#
###AUTOSAVE###
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
/dev/ttyS4 uart 16650V2 port 0xe050 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS5 uart 16650V2 port 0xe040 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS6 uart 16650V2 port 0xe030 irq 17 baud_base 115200 spd_normal skip_test
/dev/ttyS7 uart 16650V2 port 0xe020 irq 17 baud_base 115200 spd_normal skip_test
/dev/ttyS8 uart 16650V2 port 0xe010 irq 18 baud_base 115200 spd_normal skip_test
/dev/ttyS9 uart 16650V2 port 0xe000 irq 19 baud_base 115200 spd_normal skip_test
```

---

