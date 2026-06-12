---
title: "Cannot change resolution on laptop"
date: 2010-03-21
forum: Hardware
---

### Post by dimoftheyard on 2010-03-21
Hello forum,

I have Kubuntu 9.10 running on a Dell Vostro 1720 with 17" display with a resolution of 1920x1200. The graphics card is a GeForce 9600M GS and I am using the nvidia driver for it. At 1920x1200 everything works really well, my problem is that I can't change to a lower resolution. I've tried adding new resolutions in xorg.conf, 
but that just resulted in warnings like 
(WW) NVIDIA(0): No valid modes for "DFP:640x480+0+0"; removing.
in the Xorg.0.log. I've also played around with xrandr, but there I could not add new modes, because I failed to figure out how to call my output...

After some searching I found out about EDID, and tried get-edid, which got me an error message:
```
$ sudo get-edid
get-edid: get-edid version 2.0.0

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination does not support DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
```

So it looks like this could be the problem. But I hesitated to use Options like IgnoreEDID because I really do not want to inflict any damage to my display... This is a laptop, and it would be pretty worthless with the display broke. Can anybody tell me how I could convince XServer of allowing other resolutions as well?

Thank you all in advance!

---

### Post by dimoftheyard on 2010-03-21
Now I managed to get one step further with xrandr. It took me literally days to figure out that my outputs name is "default"...
Anyway, now I can create new modes and get this error
```
$ cvt 640 480
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
$ xrandr --newmode "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
$ xrandr --addmode default 640x480_60.00
$ xrandr --output default --mode 640x480_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  20
  Current serial number in output stream:  21

```

Funnily though, the last command only shows this error every second time I run it. The other times the screen goes mostly black (still showing some parts of my yakuake-terminal though, the resolution still is the old one) and then says
```
xrandr: Configure crtc 0 failed
```

Can anybody help me out there?

---

### Post by dimoftheyard on 2010-03-24
Can't anybody help me out? I tried a lot already but I am no expert and don't know what I could try next.

---

