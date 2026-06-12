---
title: "Ubuntu 8.04 LTS Internet Connection"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by ravenclair3 on 2009-04-25
Hello,

This is my first time to install Ubuntu/Linux and I would like to ask for help regarding connection to the internet. I have successfully installed Ubuntu and I could not connect to my wireless network. I have the information below. I hope someone can help:

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:9f:c5:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:646180402 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:215 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75300 (73.5 KB)  TX bytes:75300 (73.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:0f:eb:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-0F-EB-E0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: d0000000-d2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 90e0 [size=32]
    Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 90c0 [size=32]
    Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at df404c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at df400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: de300000-df3fffff
    Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
    Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: dd300000-de2fffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
    Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: dc200000-dd2fffff
    Prefetchable memory behind bridge: 00000000d5000000-00000000d5ffffff
    Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: db200000-dc1fffff
    Prefetchable memory behind bridge: 00000000d6000000-00000000d70fffff
    Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: da100000-db1fffff
    Prefetchable memory behind bridge: 00000000d7100000-00000000d80fffff
    Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: d9100000-da0fffff
    Prefetchable memory behind bridge: 00000000d8100000-00000000d90fffff
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 90a0 [size=32]
    Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 9080 [size=32]
    Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 9060 [size=32]
    Capabilities: <access denied>

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 9040 [size=32]
    Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at df404800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 216
    I/O ports at 9108 [size=8]
    I/O ports at 9114 [size=4]
    I/O ports at 9100 [size=8]
    I/O ports at 9110 [size=4]
    I/O ports at 9020 [size=32]
    Memory at df404000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: medium devsel, IRQ 11
    Memory at df405000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 9000 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e8 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 8000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>

02:00.0 Multimedia controller: Philips Semiconductors Unknown device 7160 (rev 03)
    Subsystem: Avermedia Technologies Inc Unknown device 0a55
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at de300000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

04:00.0 Network controller: Intel Corporation Unknown device 4237
    Subsystem: Intel Corporation Unknown device 1211
    Flags: bus master, fast devsel, latency 0, IRQ 214
    Memory at dc200000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 215
    I/O ports at 3000 [size=256]
    Memory at d6010000 (64-bit, prefetchable) [size=4K]
    Memory at d6000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d6020000 [disabled] [size=64K]
    Capabilities: <access denied>

06:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100300 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381 (prog-if 01)
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at da100200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
    Subsystem: Hewlett-Packard Company Unknown device 30f7
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at da100000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

---

### Post by ravenclair3 on 2009-04-27
hello?

---

### Post by vonti on 2009-05-18
run this command in ```
sudo -l
``` mode and next give me the output of ```
lspci
```

---

