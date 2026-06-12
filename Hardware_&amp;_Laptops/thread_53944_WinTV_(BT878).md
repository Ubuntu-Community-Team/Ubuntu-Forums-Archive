---
title: "WinTV (BT878)"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by mcmuffy on 2005-08-02
I am having problems getting my TV card to work. As far as I can tell it has been detected but all I get from tvtime and xawtv is a blue 'no signal' screen.
I have searched through previous posts and as far as I can tell the card should work, or am I missing something obvious?

bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 16, latency: 32, mmio: 0xdf000000
bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
bttv0: using: Hauppauge (bt878) [card=10,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
bttv0: Hauppauge eeprom: model=44805, tuner=Philips FI1246 MK2 (1), radio=no
bttv0: using tuner=1
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok
bttv0: timeout: drop=290 irq=27811/118525, risc=2a081024, bits: HSYNC OFLOW FDSRbttv0: reset, reinitialize
bttv0: PLL: 28636363 => 35468950 . ok

Thanks in advance for any and all help.
Ray

---

