---
title: "[SOLVED] Hacking a Tuner Card - Question"
date: 2008-08-15
forum: General Help
---

### Post by yojimba on 2008-08-15
I've got a question about forcing a pci card to be recognized as something its not . . . 

Looking at the following taken from the TVLINUX WIKI:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 Sample kernel output

Currently, you will find the following in the output of dmesg or your kernel logs:

saa7133[0]: found at 0000:04:08.0, rev: 16, irq: 19, latency: 64, mmio: 
0xfeaff800
saa7133[0]: subsystem: 107d:6670, board: UNKNOWN/GENERIC 
[card=0,autodetected]
saa7133[0]: board init: gpio is a022000
saa7133[0]: i2c eeprom 00: 7d 10 70 66 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7133[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 04 08 ff 00 a8 ff ff ff ff
saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 40: ff 18 00 c2 86 00 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0

However, if you add

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90

to modprobe.conf, and have the necessary nxt2004 firmware properly in place, then you will be able to force the card to be recognized and configured as if it were the KWorld ATSC 110. 
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

Here is my question. If I am looking at the generic cards address saa7133 above wouldn't I want to reference it in the modprobe.conf rather than saa7134? Or am I mistaken?

---

