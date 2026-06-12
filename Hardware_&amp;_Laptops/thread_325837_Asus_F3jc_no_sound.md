---
title: "Asus F3jc no sound"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by clapton on 2006-12-26
Hi people, I've got a asus F3JC core 2 duo 5500 and I haven't sound m of anykind.
I do the ubuntu hardware and send (auto) to a server, is anything that I can do?

Thx

---

### Post by Holser on 2006-12-26
Can you issue the following commands and paste the results here

aplay -a

lspci -v

lsmod| grep snd

sudo dpkg -l|grep alsa

---

### Post by clapton on 2006-12-26
there it is

> aplay -a
aplay: invalid option -- a



> 
lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f9f00000-fdffffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000dde00000
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1338
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe000000-fe0fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fe100000-fe1fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe200000-fe9fffff
        Prefetchable memory behind bridge: 00000000ddf00000-00000000dfe00000
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 50
        Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: fea00000-feafffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1212
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
        Flags: bus master, fast devsel, latency 0, IRQ 169
        I/O ports at c800 [size=256]
        Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fe0e0000 [disabled] [size=64K]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

06:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 5
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: medium devsel, IRQ 5
        Memory at feafec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

marco@2l33t4u:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f9f00000-fdffffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000dde00000
        Capabilities: [88] #0d [0000]
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1338
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe000000-fe0fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fe100000-fe1fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe200000-fe9fffff
        Prefetchable memory behind bridge: 00000000ddf00000-00000000dfe00000
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 50
        Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: fea00000-feafffff
        Capabilities: [50] #0d [0000]

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1212
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
        Flags: bus master, fast devsel, latency 0, IRQ 169
        I/O ports at c800 [size=256]
        Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fe0e0000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

06:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: bus master, medium devsel, latency 0, IRQ 5
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1317
        Flags: medium devsel, IRQ 5
        Memory at feafec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2


>  lsmod| grep snd 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

> sudo dpkg -l|grep alsa
ii  alsa-base                                  1.0.11-5ubuntu1                      ALSA driver configuration files
ii  alsa-utils                                 1.0.11-6ubuntu2                      ALSA utilities
ii  gstreamer0.10-alsa                         0.10.10-1ubuntu1                     GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.36-3ubuntu3                      Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                         1.10.2.dfsg-0ubuntu3                 Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.10-3ubuntu2                      Simple DirectMedia Layer (with X11 and ALSA 


---

