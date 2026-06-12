---
title: "I quit &quot;tvtime&quot;, but sound is going on"
date: 2010-10-06
forum: Hardware
---

### Post by kettlear on 2010-10-06
[B]At first, I'm not goot at English. Please excuse me.

Afer struggle to watch tv on ubuntu system, I made it.
I add "saa7134 card=40 tuner=41" in "/etc/modules".
And install tvtime then run it. Video and sound are both ok.

Here's the problem. Although I quit the "tvtime" program, sound is alive.
Of cource I can't see video, but can hear sound.

Please tell me the way I can fix it. and I paste some informations below.

dmesg|grep saa  --->
[    9.088236] saa7130/34: v4l2 driver version 0.2.15 loaded
[    9.088281] saa7134 0000:08:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.088286] saa7130[0]: found at 0000:08:05.0, rev: 1, irq: 21, latency: 16,      mmio: 0xfd5ff000
[    9.088291] saa7130[0]: subsystem: 185b:c100, board: Compro VideoMate TV PVR/FM [card=40,insmod option]
[    9.088302] saa7130[0]: board init: gpio is 400000
[    9.088373] input: saa7134 IR (Compro VideoMate TV as /devices/pci0000:00/0000:00:1e.0/0000:08:05.0/input/input5
[    9.088426] IRQ 21/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.240515] saa7130[0]: i2c eeprom 00: 5b 18 00 c1 ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240524] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240532] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240540] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240548] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240555] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff 04 ff 00 05 30 41 cb
[    9.240563] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240571] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240579] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240587] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240595] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240603] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240610] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240618] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240626] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.240634] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264565] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[    9.284622] saa7130[0]: registered device video0 [v4l2]
[    9.284691] saa7130[0]: registered device vbi0
[    9.284752] saa7130[0]: registered device radio0
[    9.289060] saa7134 ALSA driver for DMA sound loaded
[    9.289062] saa7130[0]/alsa: Compro VideoMate TV PVR/FM doesn't support digital audio

lspci -v  ---->
08:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Subsystem: Compro Technology, Inc. Device c100
    Flags: bus master, medium devsel, latency 16, IRQ 21
    Memory at fd5ff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134
    Kernel modules: saa7134

08:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Flags: bus master, medium devsel, latency 16, IRQ 19
    I/O ports at 9e00 [size=256]
    Memory at fd5fe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

[/B]****

---

