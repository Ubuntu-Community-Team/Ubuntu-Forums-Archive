---
title: "Hp Pavilion dv9033cl laptop Sound card problem.! 82801gbm"
date: 2009-03-04
forum: Hardware
---

### Post by mordeth89 on 2009-03-04
Hi I have Hp Pavilion dv9033cl (9000 series) laptop, with

conexant cx20549 intel 82801gbm ich8m high definition  Audio device.

I have Ubuntu 8.04 on. I used to have sound and everything two days ago.. Then i was in a hurry once, and switched of very rapidly pressing the shutdown key for a few seconds (i think it was stuck by that moment). When i logged in ubuntu again i had no sound.
I tried a few stuff i found on the net, nothing seemed to work.. Any idea what i Can do to make it work?


I would apreciate Any help..! thank you.







```

00:1b.0 0403: 8086:27d8 (rev 02)
   Subsystem: 103c:30bb
   Flags: bus master, fast devsel, latency 0, IRQ 21
   Memory at de300000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: [50] Power Management version 2
   Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
   Capabilities: [70] Express Unknown type IRQ 0

```






```

Codec: Conexant CX20549 (Venice)
Address: 0
Vendor Id: 0x14f15045
Subsystem Id: 0x103c30bb
Revision Id: 0x100100
Modem Function Group: 0x2
Default PCM:
   rates [0x140]: 48000 96000
   bits [0xe]: 16 20 24
   formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x10 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
 Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-Out vals:  [0x23 0x23]
 Pincap 0x0810014: OUT EAPD Detect
 EAPD 0x2: EAPD
 Pin Default 0x90170110: [Fixed] Speaker at Int N/A
   Conn = Analog, Color = Unknown
   DefAssociation = 0x1, Sequence = 0x0
   Misc = NO_PRESENCE
 Pin-ctls: 0x40: OUT
 Unsolicited: tag=00, enabled=0
 Power: setting=D0, actual=D0
 Connection: 2
    0x19 0x17*
Node 0x11 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
 Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-Out vals:  [0x23 0x23]
 Pincap 0x08113c: IN OUT HP Detect
   Vref caps: HIZ 80
 Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
   Conn = 1/8, Color = Green
   DefAssociation = 0x1, Sequence = 0xf
 Pin-ctls: 0xc0: OUT HP VREF_HIZ
 Unsolicited: tag=37, enabled=1
 Power: setting=D0, actual=D0
 Connection: 2
    0x19 0x17*
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
 Amp-Out caps: ofs=0x2b, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-Out vals:  [0xab 0xab]
 Pincap 0x08113c: IN OUT HP Detect
   Vref caps: HIZ 80
 Pin Default 0x01813030: [Jack] Line In at Ext Rear
   Conn = 1/8, Color = Blue
   DefAssociation = 0x3, Sequence = 0x0
 Pin-ctls: 0x20: IN VREF_HIZ
 Unsolicited: tag=00, enabled=0
 Power: setting=D0, actual=D0
 Connection: 2
    0x19* 0x17
Node 0x13 [Pin Complex] wcaps 0x400301: Stereo Digital
 Pincap 0x0810: OUT
 Pin Default 0x21447040: [Jack] SPDIF Out at Sep Rear
   Conn = RCA, Color = Yellow
   DefAssociation = 0x4, Sequence = 0x0
 Pin-ctls: 0x00:
 Connection: 1
    0x18
Node 0x14 [Pin Complex] wcaps 0x400081: Stereo
 Pincap 0x081124: IN Detect
   Vref caps: HIZ 80
 Pin Default 0x97a70050: [Fixed] Mic at Int Riser
   Conn = Analog, Color = Unknown
   DefAssociation = 0x5, Sequence = 0x0
 Pin-ctls: 0x24: IN VREF_80
 Unsolicited: tag=00, enabled=0
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
 Pincap 0x0820: IN
 Pin Default 0x99330060: [Fixed] CD at Int ATAPI
   Conn = ATAPI, Color = Unknown
   DefAssociation = 0x6, Sequence = 0x0
 Pin-ctls: 0x00:
Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
 Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0b, mute=1
 Amp-Out vals:  [0x06]
Node 0x17 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
 Amp-In caps: ofs=0x14, nsteps=0x2b, stepsize=0x05, mute=1
 Amp-In vals:  [0x14 0x14] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
 Power: setting=D0, actual=D0
 Connection: 5
    0x19 0x14 0x12 0x11 0x15
Node 0x18 [Audio Output] wcaps 0x211: Stereo Digital
 Converter: stream=0, channel=0
 Digital:
 Digital category: 0x0
 PCM:
   rates [0x40]: 48000
   bits [0x6]: 16 20
   formats [0x5]: PCM AC3
Node 0x19 [Audio Output] wcaps 0xc11: Stereo R/L
 Converter: stream=0, channel=0
 PCM:
   rates [0x540]: 48000 96000 192000
   bits [0xe]: 16 20 24
   formats [0x1]: PCM
 Power: setting=D0, actual=D0
Node 0x1a [Audio Input] wcaps 0x100d0b: Stereo Amp-In R/L
 Amp-In caps: ofs=0x00, nsteps=0x17, stepsize=0x05, mute=1
 Amp-In vals:  [0x17 0x17] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
 Converter: stream=0, channel=0
 SDI-Select: 0
 Power: setting=D0, actual=D0
 Connection: 5
    0x17 0x14* 0x12 0x11 0x15
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono















```

---

