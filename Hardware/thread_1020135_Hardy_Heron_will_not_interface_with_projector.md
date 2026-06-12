---
title: "Hardy Heron will not interface with projector"
date: 2008-12-23
forum: Hardware
---

### Post by eagle416 on 2008-12-23
I have a Dell Latitude D610 on Kubuntu 8.04. Windows is able to pick up a projector and work with it immediately. Kubuntu, not so lucky.

When I connect a projector the projector continues to say "searching.....". I've hit the CRT/LCD select button many times. Nothing changes.

Can anybody help? I ran an lspci -v. Here's what I have.

```
eagle416@PEACH:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Dell Dell Latidude C610
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec38 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Dell Unknown device 0182
        Flags: bus master, fast devsel, latency 0
        Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: dfd00000-dfdfffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
        Memory behind bridge: dfc00000-dfcfffff
        Capabilities: [50] Subsystem: Dell Unknown device 0182

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Latitude D610 Laptop
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ed00 [size=256]
        I/O ports at ec40 [size=64]
        Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
        Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Conexant Unknown device 5423
        Flags: medium devsel, IRQ 18
        I/O ports at ee00 [size=256]
        I/O ports at ec80 [size=128]
        Capabilities: [50] Power Management version 2

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Dell Unknown device 0182
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]
        Capabilities: [70] Power Management version 2

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
        Subsystem: Dell Latitude D610
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
        Subsystem: Dell Unknown device 0182
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dfc00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
        Subsystem: Dell Unknown device 0182
        Flags: medium devsel, IRQ 5
        Memory at dfcfd000 (32-bit, non-prefetchable) [size=4K]
        Memory at dfcfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Dell B130 laptop integrated WLAN
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
```

---

### Post by rjr162 on 2008-12-23
Have you tried rebooting?  I know it's a pain, but I have a Dell Inspiron and when I plugged in a second monitor or projector in 8.04 or 8.10, I had to reboot before the output would work.  You could have the binary driver or whatever find the 2nd monitor, etc, but there wouldn't be a picture until you actually rebooted.

You could also try CTRL+ALT+BACKSPACE to restart X, but if I remember correctly that didn't make the 2nd monitor work for me, I had to reboot.

---

### Post by eagle416 on 2008-12-24
thanks. next time I'm near a projector I'll try it.

---

### Post by namdung on 2008-12-24
Press *Fn Key + CRT/LCD *

---

### Post by eagle416 on 2008-12-26
that's the problem. Hitting that button does nothing.

---

