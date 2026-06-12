---
title: "Suspend/Resume Freeze with WinTV Card"
date: 2008-08-12
forum: General Help
---

### Post by browndog289 on 2008-08-12
Hello

My Ubuntu system was working well with only the occasional freeze when I suspended it.

However at the weekend I installed an old PCI WinTV card I had and ever since then it freezes when it resumes from suspend. Sometimes I get a grey box with nothing in it - this is the enter password box but with nothing there. The mouse and keyboard are also unresponsive.

When I wake it from suspend by moving the mouse or pressing on the keyboard I see an error message repeated several times - the message is:

MSP3400 - Chip reset failed

I think MSP3400 is related to my WinTV card. 

lspci gives:

03:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
03:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

lsmod gives:

bt878                  13672  0 
bttv                  214772  1 bt878

dmesg gives:

[   37.321604] bttv0: Bt878 (rev 2) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xf8fff000
[   37.322782] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   37.322786] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   37.322819] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   37.325325] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   37.351500] tveeprom 1-0050: Hauppauge model 61324, rev D108, serial# 3377109
[   37.351502] tveeprom 1-0050: tuner model is Philips FI1216 MK2 (idx 8, type 5)
[   37.351504] tveeprom 1-0050: TV standards PAL(B/G) (eeprom 0x04)
[   37.351506] tveeprom 1-0050: audio processor is MSP3415 (idx 6)
[   37.351507] tveeprom 1-0050: has radio
[   37.351509] bttv0: Hauppauge eeprom indicates model#61324
[   37.351510] bttv0: tuner type=5
[   37.351692] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   37.378193] msp3400 1-0040: MSP3410D-B4 found @ 0x80 (bt878 #0 [sw])
[   37.378196] msp3400 1-0040: MSP3410D-B4 supports nicam, mode is autodetect
[   37.391717] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   37.392311] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   37.623337] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   37.623361] tuner-simple 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   37.623363] tuner 1-0061: type set to Philips PAL_BG (FI1
[   37.623365] tuner-simple 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   37.623367] tuner 1-0061: type set to Philips PAL_BG (FI1
[   37.630094] bttv0: registered device video0
[   37.630112] bttv0: registered device vbi0
[   37.630124] bttv0: registered device radio0
[   37.644765] bttv0: PLL: 28636363 => 35468950 .. ok

So I can't use suspend at the moment. Can anyone help? Are there any modules I need to change or edit in the acpi scripts?

Thanks

---

### Post by SteveGodfrey on 2008-12-27
Did you ever solve this?

---

