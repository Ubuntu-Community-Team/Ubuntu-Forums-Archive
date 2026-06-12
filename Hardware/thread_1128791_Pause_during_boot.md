---
title: "Pause during boot"
date: 2009-04-18
forum: Hardware
---

### Post by eje211 on 2009-04-18
My Eee 4G pauses during boot every time I boot. Here's what dmesg says about the moment where it pauses:```
[   30.827181] USB Video Class driver (v0.1.0)
[   30.830000] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   31.772037] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00
000
[   31.876277] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/inpu
t/input10
[   71.066016] lp: driver loaded but no devices found
[   72.048955] Adding 224868k swap on /dev/sda5.  Priority:-1 extents:1 across:224868k
[   72.264482] EXT3 FS on sda1, internal journal
[   72.641485] kjournald starting.  Commit interval 5 seconds

```There's a clear 40 second gap.

What can I do about it? I don't see anything in the dmesg that shows what could cause the stop. Where should I look?

Thanks to anyone who can help.

---

### Post by jerrrys on 2009-04-18
if u are using two screens,try disconnect usb video driver

---

### Post by eje211 on 2009-04-19
I'm only using one screen, but will look in the BIOS to see if I find something.

---

