---
title: "Please help tv tunner stopped working when upgrading to 8.04"
date: 2008-11-28
forum: General Help
---

### Post by anewbie on 2008-11-28
I had been using my tv tuner (a very old model) with the previous version of linux (7.x). I upgraded a few minutes ago to 8.04 and it stopped working.

I normally use tvtime. The dmesg which describes the tvtuner prior to upgrade is:
Nov 28 12:51:57 pc1 kernel: [   93.964565] bttv: driver version 0.9.17 loaded
Nov 28 12:51:57 pc1 kernel: [   93.964568] bttv: using 8 buffers with 2080k
(520 pages) each for capture
Nov 28 12:51:57 pc1 kernel: [   93.964609] bttv: Bt8xx card found (0).
Nov 28 12:51:57 pc1 kernel: [   93.964618] ACPI: PCI Interrupt 0000:05:02.0[A]
-> GSI 23 (level, low) -> IRQ 19
Nov 28 12:51:57 pc1 kernel: [   93.964628] bttv0: Bt878 (rev 2) at
0000:05:02.0, irq: 19, latency: 64, mmio: 0xdfefe000
Nov 28 12:51:57 pc1 kernel: [   93.964636] bttv0: detected: Hauppauge WinTV
[card=10], PCI subsystem ID is 0070:13eb
Nov 28 12:51:57 pc1 kernel: [   93.964638] bttv0: using: Hauppauge (bt878)
[card=10,autodetected]
Nov 28 12:51:57 pc1 kernel: [   93.967147] bttv0: Hauppauge/Voodoo msp34xx:
reset line init [5]
---
after upgrade I see:
Nov 28 15:33:09 pc1 kernel: [   94.182403] bttv: driver version 0.9.17 loaded
Nov 28 15:33:09 pc1 kernel: [   94.182407] bttv: using 8 buffers with 2080k (520 pages) each for capture
Nov 28 15:33:09 pc1 kernel: [   94.553348] bttv: Bt8xx card found (0).
Nov 28 15:33:09 pc1 kernel: [   94.553370] bttv0: Bt878 (rev 2) at 0000:05:02.0, irq: 19, latency: 64, mmio: 0xdfefe000
Nov 28 15:33:09 pc1 kernel: [   94.553589] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
Nov 28 15:33:09 pc1 kernel: [   94.553591] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
Nov 28 15:33:09 pc1 kernel: [   94.556099] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
Nov 28 15:33:09 pc1 kernel: [   94.587327] bttv0: Hauppauge eeprom indicates model#61381
Nov 28 15:33:09 pc1 kernel: [   94.587329] bttv0: tuner type=0
Nov 28 15:33:09 pc1 kernel: [   94.593073] bttv0: i2c: checking for MSP34xx @ 0x80... found
Nov 28 15:33:09 pc1 kernel: [   94.623535] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
Nov 28 15:33:09 pc1 kernel: [   94.624135] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
Nov 28 15:33:09 pc1 kernel: [   94.748142] bttv0: registered device video0
Nov 28 15:33:09 pc1 kernel: [   94.748163] bttv0: registered device vbi0
Nov 28 15:33:09 pc1 kernel: [   94.748182] bttv0: registered device radio0
Nov 28 15:33:09 pc1 kernel: [   94.766106] bttv0: PLL: 28636363 => 35468950 .. ok
Nov 28 15:37:32 pc1 kernel: [  362.023426] bttv0: PLL can sleep, using XTAL (28636363).
----
which seems nearly identical yet tvtime no longer works. Any suggestion or hints ?

---

### Post by anewbie on 2008-11-28
ok i have no idea why but after a couple of reboots it seems to work sort of - video is a bit static but ok i guess and sound is off and can only be controlled via the intel hda (not the volume bar on the aplet). Kind of painful but at least it works - everything worked fine prior to upgrade. I guess upgrading was a bad idea and a step backwards :(

---

