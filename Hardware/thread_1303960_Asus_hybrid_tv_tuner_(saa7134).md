---
title: "Asus hybrid tv tuner (saa7134)"
date: 2009-10-28
forum: Hardware
---

### Post by hazz on 2009-10-28
Hello everyone

I know there are loads of threads discussing this tv tuner, I apologize in advance for starting yet another one. I have read many of the threads and googled lots with no results, so any help is very appreciated.

I'll explain my problem. I have followed the instructions from the Linux tv wiki, but that does not seem to work for me. I think the card is recognised and everything, but tvtime and other software I tried report no signal. So effectively it is useless.

Output of lspci -vvnn:
```

04:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:48ae]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at dfafa000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```and this is what dmesg says:
```

[    9.358842] saa7130/34: v4l2 driver version 0.2.15 loaded
[    9.358899] saa7134 0000:04:07.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.358905] saa7133[0]: found at 0000:04:07.0, rev: 209, irq: 17, latency: 32, mmio: 0xdfafa000
[    9.358911] saa7133[0]: subsystem: 1043:48ae, board: ASUSTeK P7131 Hybrid [card=112,insmod option]
[    9.358925] saa7133[0]: board init: gpio is 0
[    9.358931] saa7133[0]: gpio: mode=0x0000000 in=0x0000000 out=0x0000000 [pre-init]
[    9.358990] input: saa7134 IR (ASUSTeK P7131 Hybri as /devices/pci0000:00/0000:00:13.1/0000:04:07.0/input/input12
[    9.359029] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.508041] saa7133[0]: i2c eeprom 00: 43 10 ae 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    9.508056] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    9.508070] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 00 01 03 08 ff 00 0c ff ff ff ff
[    9.508084] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508097] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 22 15 10 ff ff ff ff ff ff
[    9.508110] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508124] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508137] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508151] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508164] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508181] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508190] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508199] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508208] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508217] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.508225] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.516019] saa7133[0]: i2c scan: found device @ 0x10  [???]
[    9.533609] saa7133[0]: i2c scan: found device @ 0x96  [???]
[    9.540017] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[    9.840133] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   13.528096] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   13.528159] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   13.528294] saa7133[0]: dsp access error
[   13.528386] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   13.596113] saa7133[0]: registered device video0 [v4l2]
[   13.596144] saa7133[0]: registered device vbi0
[   13.596188] saa7133[0]: registered device radio0
[   13.684377] saa7134 ALSA driver for DMA sound loaded
[   13.684388] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.684405] saa7133[0]/alsa: saa7133[0] at 0xdfafa000 irq 17 registered as card -2
[   13.728146] DVB: registering new adapter (saa7133[0])
[   14.520978] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Radio]
[   15.964136] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   16.020610] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   44.717714] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Radio]
[   46.256100] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   46.304612] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   47.835978] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   47.836328] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   47.836848] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   47.837040] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   47.838894] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[   53.535455] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  132.876079] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  133.732087] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  135.936059] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  148.433056] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite1]
[  148.433148] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite1]
[  148.578298] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite1]
[  149.194920] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite2]
[  149.195000] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite2]
[  149.834936] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [S-Video]
[  149.835033] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [S-Video]
[  151.976075] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  152.832467] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  153.835425] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite1]
[  153.835517] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite1]
[  153.978781] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite1]
[  158.275901] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite2]
[  158.275981] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [Composite2]
[  161.076258] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [S-Video]
[  161.076354] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0200000 [S-Video]
[  167.380087] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  168.270981] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  235.405631] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  235.405725] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]
[  235.484598] saa7133[0]: gpio: mode=0x0200000 in=0x0000000 out=0x0000000 [Television]

```I believe the card to be [http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-P7131_Hybrid](http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-P7131_Hybrid), but I might be wrong, it shipped with a packard bell ixtreme x2711 if that helps.

One thing I noticed is the hardware ID 1043:48ae, which I cannot find reference to anywhere. If someone out there managed to get this card working then please let me know what you did. Also, if you believe it is incompatible and that's that, then just put me out of my misery :)

**UPDATE:**

Tv time seems to have found a few channels no, so if anyone has the same problem and would like help, let me know.

I did:
```

sudo gedit /etc/modprobe.d/saa7134.conf

```and added:
```

options saa7134 card=112 tuner=54 gpio_tracking=1 i2c_scan=1

```I'll let you know if I get all the right channels or not.

---

### Post by hazz on 2009-10-29
Unfortunately it turns out I am only getting the terrestrial channels (all 5 of them) and these are being phased out here (UK).

Has anyone managed to get DVB working with this tuner?

Forgot to mention, I am using Karmik x86 (32 bit) and I compiled and installed the latest saa7134 from the mercurial trunk (linux tv wiki claimed it is more stable than the kernel one)

Let me know if you need more information to help.

---

### Post by hazz on 2009-10-29
So no one has encountered this card before then.

Okay, cheers.

---

### Post by mehturt on 2010-01-22
I have the same (similar? saa7133[0]: subsystem: 1043:4876, board: ASUSTeK P7131 Hybrid [card=112,autodetected]) card.  DVB works for me in mythtv, but I don't have the right antena so the signal is weak; analog channels don't work very well, have some issues with it.
I'm trying to get the remote working properly now.

---

