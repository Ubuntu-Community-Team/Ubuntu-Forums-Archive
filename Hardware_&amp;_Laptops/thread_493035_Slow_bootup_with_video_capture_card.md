---
title: "Slow bootup with video capture card"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by houstonbofh on 2007-07-05
I have a somewhat odd problem, that seems to leave everyone stumped. Fresh Feisty install, and everything is fine. I installed a cheap 8 port, 8 chip conexiant based bt878 video capture card. With a redhat LiveCD, everything is fine. When booting in ubuntu, however, bootup takes a loooooooong time. I am thinking this has to do with hardware detection. See the relevant parts of my dmesg below. Any thoughts on how to speed up the boot process?

```
[   14.682375] Linux video capture interface: v2.00
[   14.758420] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   14.766337] bttv: driver version 0.9.16 loaded
[   14.766341] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   14.766402] bttv: Bt8xx card found (0).
[   14.766437] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 22 (level, low) -> IRQ 20
[   14.766459] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 20, latency: 64, mmio: 0xfaffe000
[   14.766470] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   14.766505] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   15.026011] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   15.075316] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 21
[   15.075350] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   15.495225] intel8x0_measure_ac97_clock: measured 52232 usecs
[   15.495229] intel8x0: clocking to 48000
[   27.540661] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   27.540667] bttv0: using tuner=-1
[   27.540671] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   33.928755] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   40.316846] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   46.704937] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   53.093089] bttv0: registered device video0
[   53.093116] bttv0: registered device vbi0
[   53.093163] bttv: Bt8xx card found (1).
[   53.093198] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 23 (level, low) -> IRQ 19
[   53.093217] bttv1: Bt878 (rev 17) at 0000:02:09.0, irq: 19, latency: 64, mmio: 0xfaffc000
[   53.093243] bttv1: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   53.093278] bttv1: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   65.869211] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   65.869216] bttv1: using tuner=-1
[   65.869219] bttv1: i2c: checking for MSP34xx @ 0x80... not found
[   72.257305] bttv1: i2c: checking for TDA9875 @ 0xb0... not found
[   78.645396] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[   85.033489] bttv1: i2c: checking for TDA9887 @ 0x86... not found
[   91.421630] bttv1: registered device video1
[   91.421655] bttv1: registered device vbi1
[   91.421697] bttv: Bt8xx card found (2).
[   91.421731] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 20 (level, low) -> IRQ 22
[   91.421746] bttv2: Bt878 (rev 17) at 0000:02:0a.0, irq: 22, latency: 64, mmio: 0xfaffa000
[   91.421766] bttv2: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   91.421798] bttv2: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  104.197763] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[  104.197767] bttv2: using tuner=-1
[  104.197770] bttv2: i2c: checking for MSP34xx @ 0x80... not found
[  110.585855] bttv2: i2c: checking for TDA9875 @ 0xb0... not found
[  116.973948] bttv2: i2c: checking for TDA7432 @ 0x8a... not found
[  123.362039] bttv2: i2c: checking for TDA9887 @ 0x86... not found
[  129.750178] bttv2: registered device video2
[  129.750203] bttv2: registered device vbi2
[  129.750246] bttv: Bt8xx card found (3).
[  129.750279] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 21 (level, low) -> IRQ 23
[  129.750293] bttv3: Bt878 (rev 17) at 0000:02:0b.0, irq: 23, latency: 64, mmio: 0xfaff8000
[  129.750312] bttv3: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[  129.750346] bttv3: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  142.526313] tveeprom 3-0050: Huh, no eeprom present (err=-121)?
[  142.526318] bttv3: using tuner=-1
[  142.526320] bttv3: i2c: checking for MSP34xx @ 0x80... not found
[  148.914407] bttv3: i2c: checking for TDA9875 @ 0xb0... not found
[  155.302498] bttv3: i2c: checking for TDA7432 @ 0x8a... not found
[  161.690591] bttv3: i2c: checking for TDA9887 @ 0x86... not found
[  168.078728] bttv3: registered device video3
[  168.078752] bttv3: registered device vbi3
[  168.078797] bttv: Bt8xx card found (4).
[  168.078824] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 22 (level, low) -> IRQ 20
[  168.078837] bttv4: Bt878 (rev 17) at 0000:02:0c.0, irq: 20, latency: 64, mmio: 0xfaff6000
[  168.078854] bttv4: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[  168.078884] bttv4: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  180.854865] tveeprom 4-0050: Huh, no eeprom present (err=-121)?
[  180.854869] bttv4: using tuner=-1
[  180.854872] bttv4: i2c: checking for MSP34xx @ 0x80... not found
[  187.242957] bttv4: i2c: checking for TDA9875 @ 0xb0... not found
[  193.631050] bttv4: i2c: checking for TDA7432 @ 0x8a... not found
[  200.019144] bttv4: i2c: checking for TDA9887 @ 0x86... not found
[  206.407287] bttv4: registered device video4
[  206.407311] bttv4: registered device vbi4
[  206.407356] bttv: Bt8xx card found (5).
[  206.407392] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 23 (level, low) -> IRQ 19
[  206.407408] bttv5: Bt878 (rev 17) at 0000:02:0d.0, irq: 19, latency: 64, mmio: 0xfaff4000
[  206.407432] bttv5: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[  206.407467] bttv5: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  219.183414] tveeprom 5-0050: Huh, no eeprom present (err=-121)?
[  219.183420] bttv5: using tuner=-1
[  219.183423] bttv5: i2c: checking for MSP34xx @ 0x80... not found
[  225.571505] bttv5: i2c: checking for TDA9875 @ 0xb0... not found
[  231.959597] bttv5: i2c: checking for TDA7432 @ 0x8a... not found
[  238.347689] bttv5: i2c: checking for TDA9887 @ 0x86... not found
[  244.737602] bttv5: registered device video5
[  244.737873] bttv5: registered device vbi5
[  244.737921] bttv: Bt8xx card found (6).
[  244.737959] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 20 (level, low) -> IRQ 22
[  244.737976] bttv6: Bt878 (rev 17) at 0000:02:0e.0, irq: 22, latency: 64, mmio: 0xfaff2000
[  244.738006] bttv6: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[  244.738036] bttv6: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  257.511968] tveeprom 6-0050: Huh, no eeprom present (err=-121)?
[  257.511973] bttv6: using tuner=-1
[  257.511976] bttv6: i2c: checking for MSP34xx @ 0x80... not found
[  263.900060] bttv6: i2c: checking for TDA9875 @ 0xb0... not found
[  270.288152] bttv6: i2c: checking for TDA7432 @ 0x8a... not found
[  276.676243] bttv6: i2c: checking for TDA9887 @ 0x86... not found
[  283.064391] bttv6: registered device video6
[  283.064415] bttv6: registered device vbi6
[  283.064461] bttv: Bt8xx card found (7).
[  283.064492] ACPI: PCI Interrupt 0000:02:0f.0[A] -> GSI 21 (level, low) -> IRQ 23
[  283.064507] bttv7: Bt878 (rev 17) at 0000:02:0f.0, irq: 23, latency: 64, mmio: 0xfaff0000
[  283.064529] bttv7: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[  283.064560] bttv7: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  295.840518] tveeprom 7-0050: Huh, no eeprom present (err=-121)?
[  295.840523] bttv7: using tuner=-1
[  295.840527] bttv7: i2c: checking for MSP34xx @ 0x80... not found
[  302.228611] bttv7: i2c: checking for TDA9875 @ 0xb0... not found
[  308.616703] bttv7: i2c: checking for TDA7432 @ 0x8a... not found
[  315.004795] bttv7: i2c: checking for TDA9887 @ 0x86... not found
[  321.392939] bttv7: registered device video7
[  321.392967] bttv7: registered device vbi7
[  321.395398] lp: driver loaded but no devices found
[  321.423509] Adding 1485972k swap on /dev/disk/by-uuid/51ebdb03-cb92-4d6b-8419-550147ceb27e.  Priority:-1 extents:1 across:1485972k
[  321.424452] bt878: AUDIO driver version 0.0.0 loaded
[  321.424501] bt878: Bt878 AUDIO function found (0).
[  321.424532] ACPI: PCI Interrupt 0000:02:08.1[A] -> GSI 22 (level, low) -> IRQ 20
[  321.424540] bt878_probe: card id=[0x0],[ <NULL> ] has DVB functions.
[  321.424552] bt878(0): Bt878 (rev 17) at 02:08.1, irq: 20, latency: 64, memory: 0xfafff000
[  321.424713] bt878: Bt878 AUDIO function found (1).
[  321.424736] ACPI: PCI Interrupt 0000:02:09.1[A] -> GSI 23 (level, low) -> IRQ 19
[  321.424745] bt878_probe: card id=[0x0],[ <NULL> ] has DVB functions.
[  321.424752] bt878(1): Bt878 (rev 17) at 02:09.1, irq: 19, latency: 64, memory: 0xfaffd000
[  321.424914] bt878: Bt878 AUDIO function found (2).
[  321.424935] ACPI: PCI Interrupt 0000:02:0a.1[A] -> GSI 20 (level, low) -> IRQ 22
[  321.424943] bt878_probe: card id=[0x0],[ <NULL> ] has DVB functions.
[  321.424950] bt878(2): Bt878 (rev 17) at 02:0a.1, irq: 22, latency: 64, memory: 0xfaffb000
[  321.425101] bt878: Bt878 AUDIO function found (3).
[  321.425120] ACPI: PCI Interrupt 0000:02:0b.1[A] -> GSI 21 (level, low) -> IRQ 23
[  321.425128] bt878_probe: card id=[0x0],[ <NULL> ] has DVB functions.
[  321.425135] bt878(3): Bt878 (rev 17) at 02:0b.1, irq: 23, latency: 64, memory: 0xfaff9000
[  321.425313] bt878: Bt878 AUDIO function found (4).
[  321.425315] bt878: Too many devices inserted
[  321.425366] bt878: probe of 0000:02:0c.1 failed with error -12
[  321.425373] bt878: Bt878 AUDIO function found (4).
[  321.425375] bt878: Too many devices inserted
[  321.425417] bt878: probe of 0000:02:0d.1 failed with error -12
[  321.425425] bt878: Bt878 AUDIO function found (4).
[  321.425427] bt878: Too many devices inserted
[  321.425469] bt878: probe of 0000:02:0e.1 failed with error -12
[  321.425479] bt878: Bt878 AUDIO function found (4).
[  321.425480] bt878: Too many devices inserted
[  321.425530] bt878: probe of 0000:02:0f.1 failed with error -12
```

---

### Post by houstonbofh on 2007-07-07
Still no progress here.  Everything works fine, but it takes over 4 and a half minutes to go from GRUB to the login screen.  Does anyone have any ideas?

---

