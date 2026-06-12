---
title: "TV-card not working"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-03-08
Hi, I'm having troubles getting my tv card to work in Linux. It's a cinergy 400, with the SAA7134 chipset.

```
0000:03:03.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
```

I'm using the latest nVidia driver, kernel 2.6.8-5-686-smp, the xfree that comes with Warty. When I start xawtv I only get a black screen. Capture is then at grabdisplay. I change capture to overlay and I only get a blue screen. I change capture to off and I get a black screen. Zapping shows a blue screen only, and when I change to capture mode from overlay mode it crashes.

```
** WARNING **: Cannot set new capture format: [tveng25.c] p_tveng25_qbuf (line 1450)
VIDIOC_QBUF failed: Invalid argument
tveng25.c (1500): tveng25_start_capturing: assertion (p_info->num_buffers == 0) failed
```

```
fackamato@fackamato:~ $ zapping --device=/dev/video0
I/O error #5 in decoding thread:
V4L/V4L2 VBI interface: Failed to read from the device
Aborting.
```

```
fackamato@fackamato:~ $ lsmod | grep v4 ; lsmod | grep saa7
v4l2_common             6336  1 saa7134
v4l1_compat            14468  1 saa7134
saa7134                99280  0
video_buf              22340  1 saa7134
v4l2_common             6336  1 saa7134
v4l1_compat            14468  1 saa7134
soundcore              10688  5 snd,saa7134
ir_common               5156  1 saa7134
videodev               10144  1 saa7134
i2c_core               24064  7 tuner,saa7134,w83781d,eeprom,i2c_sensor,i2c_isa,i2c_i801
```

Anyone got any idea? Below is part of my XF86Config-4:

```
# === nVidia device section ===

Section "Device"
        Identifier                          "nVidia Graphics Adapter"
        Driver                              "nvidia"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
        #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
        Option "no_accel"                   "no"
        Option "no_dri"                     "no"
# === misc DRI settings ===
        Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
        Option          "UseInternalAGPGART"    "no"
        Option          "RenderAccel"           "true"
        Option          "VideoOverlay"          "on"
        Option "ForceGenericCPU"            "no"
        BusID "PCI:1:0:0"    # vendor=1002, device=5964
        Screen 0
EndSection
```

I'm thankful for any ideas :)

---

### Post by fackamato on 2005-03-08
dmesg:


```
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 185
saa7134[0]: found at 0000:03:03.0, rev: 1, irq: 185, latency: 32, mmio: 0xfeaffc00
saa7134[0]: subsystem: 153b:1142, board: Terratec Cinergy 400 TV [card=8,autodetected]
saa7134[0]: board init: gpio is 50000
saa7134[0]: registered input device for IR
tuner: chip found at addr 0xc0 i2c-bus saa7134[0]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by saa7134[0]
saa7134[0]: i2c eeprom 00: 3b 15 42 11 ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
```

edit: it's strange, scantv finds the channels...

---

### Post by pardasaniman on 2005-03-08
I dunno much about your card in particular... Are your permissions set up properly?   Try running with sudo?

---

### Post by fackamato on 2005-03-08
[QUOTE=pardasaniman]I dunno much about your card in particular... Are your permissions set up properly?   Try running with sudo?[/QUOTE]


Thanks for the reply. Yes, permissions are right, running as root/sudo doesn't help. :/

---

### Post by Wombley on 2005-03-08
[QUOTE=fackamato]dmesg:


```
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 185
saa7134[0]: found at 0000:03:03.0, rev: 1, irq: 185, latency: 32, mmio: 0xfeaffc00
saa7134[0]: subsystem: 153b:1142, board: Terratec Cinergy 400 TV [card=8,autodetected]
saa7134[0]: board init: gpio is 50000
saa7134[0]: registered input device for IR
tuner: chip found at addr 0xc0 i2c-bus saa7134[0]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by saa7134[0]
saa7134[0]: i2c eeprom 00: 3b 15 42 11 ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
```

edit: it's strange, scantv finds the channels...[/QUOTE]
 With my card (with BT878 chipset, graphics also nvidia), scantv finds channels but xawtv just shows a blank screen (although oddly enough I do get the sound). If I try with tvtime, after a while on scan it finds the channel and works fine. It might be worth checking to see if that works (package tvtime in universe, Channel Management -> Scan channels for signal (takes a while)).

---

### Post by fackamato on 2005-03-08
[QUOTE=Wombley]With my card (with BT878 chipset, graphics also nvidia), scantv finds channels but xawtv just shows a blank screen (although oddly enough I do get the sound). If I try with tvtime, after a while on scan it finds the channel and works fine. It might be worth checking to see if that works (package tvtime in universe, Channel Management -> Scan channels for signal (takes a while)).[/QUOTE]


I've tried with zapping, tvtime and xawtv. Either a black screen or a blue screen (overlay). No sound at all. :/

I've even upgraded to kernel 2.6.10, to no avail.

**Edit**: It works now! 2.6.10 created a /dev/video4linux device, which works perfectly. :) :D

---

### Post by Wombley on 2005-03-08
[QUOTE=fackamato]I've tried with zapping, tvtime and xawtv. Either a black screen or a blue screen (overlay). No sound at all. :/

I've even upgraded to kernel 2.6.10, to no avail.

**Edit**: It works now! 2.6.10 created a /dev/video4linux device, which works perfectly. :) :D[/QUOTE]
 Does tvtime-scanner pick the channels up? If so, when you run tvtime with -f custom does the right frequency appear on the screen? What is the output when you run tvtime -v ? (Sorry for emphasis on tvtime, just what I've had most success with).

**Edit:** Good, glad you got it working

---

### Post by Eclipser on 2005-03-26
Good for you to get that TV card working but I'm still having problems with that card (and pinnacle pctv stereo (also saa7134), I changed to terratec (from my dads computer) to see if it would work but no success).

I have 2.6.11.5 kernel and I don't have /dev/video4linux... video works fine in tvtime (xawtv and motv show just a black screen).

Could you point me to some direction, please? thanks in advance.

---

### Post by fackamato on 2005-03-26
[QUOTE=Eclipser]Good for you to get that TV card working but I'm still having problems with that card (and pinnacle pctv stereo (also saa7134), I changed to terratec (from my dads computer) to see if it would work but no success).

I have 2.6.11.5 kernel and I don't have /dev/video4linux... video works fine in tvtime (xawtv and motv show just a black screen).

Could you point me to some direction, please? thanks in advance.[/QUOTE]

What relevant devices do you have?

I have /dev/video0 .

---

### Post by Eclipser on 2005-03-26
yes, I have /dev/video0, video image is just fine and it detects all channels, but I get no sound at all, no matter what I do... setting mixer settings to correct values, unmuting with v4lctl, using different module arguments, etc... same problems on PCTV stereo

---

