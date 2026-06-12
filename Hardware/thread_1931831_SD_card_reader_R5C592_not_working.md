---
title: "SD card reader R5C592 not working"
date: 2012-02-26
forum: Hardware
---

### Post by pmurk on 2012-02-26
Hallo,
did a fresh Xubuntu 11.10 installation on my Acer Aspire 7520G today. 
So fare most thing are fine but the build in card reader does not work. 

lspci -v output gives 

```

01:04.0 Multimedia video controller: Ricoh Co Ltd Device 0032 (rev 05) (prog-if 10)
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 80000000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>

01:04.1 Unclassified device [0005]: Ricoh Co Ltd Device 0022 (rev 22)
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 80000800 (32-bit, non-prefetchable) [disabled] [size=256]
    Capabilities: <access denied>

01:04.2 Unclassified device [0080]: Ricoh Co Ltd Device 0043 (rev 12)
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 80000900 (32-bit, non-prefetchable) [disabled] [size=256]
    Capabilities: <access denied>

01:04.3 Unclassified device [0080]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Acer Incorporated [ALI] Device 0126
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 80000a00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

01:04.4 Unclassified device [0080]: Ricoh Co Ltd Device 0052 (rev 12)
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at 80000b00 (32-bit, non-prefetchable) [disabled] [size=256]
    Capabilities: <access denied>
```I have googled at lot but without success.
Any ideas?

---

