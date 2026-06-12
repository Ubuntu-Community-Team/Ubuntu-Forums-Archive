---
title: "i2c i/o errer"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by ddhytz on 2005-06-17
I am having problem with TVtime and Compro DVB T300 tv card. I have a file called saa7134 under /etc/modprobe.d. Here is dmesg before running TVtime:

[I]Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:02:07.0[A] -> GSI 16 (level, low) -> IRQ 16
saa7134[0]: found at 0000:02:07.0, rev: 1, irq: 16, latency: 64, mmio: 0xfe8dfc00
saa7134[0]: subsystem: 185b:c900, board: Compro VideoMate TV [card=19,insmod option]
saa7134[0]: board init: gpio is 853f58
saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner: chip found at addr 0xd0 i2c-bus saa7134[0]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by saa7134[0]
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0[/I]

After running TVtime, I got this eror message:

[I]tuner: i2c i/o error: rc == -5 (should be 4)
saa7134[0]/audio: audio carrier scan failed, using 5.500 MHz [default][/I]

Running tvtime-scanner gets no signal. 

Anyone can help?

---

### Post by vivichrist on 2008-04-10
I assume the tuner module didn't load. I myself am having a similar problem with hardy and tda9887 module with mt HVR3000 card.
sometimes I boot and it just works. sometimes I have to manually load the module after boot:

$ modprobe tda9887

in your case:

$ modprobe tuner

I guess? try it. this only works sometimes for me

---

