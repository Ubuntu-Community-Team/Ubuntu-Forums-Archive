---
title: "Logitech MOMO force feedback not working"
date: 2012-09-08
forum: Hardware
---

### Post by Erszebet Lunah on 2012-09-08
I'm using Kubuntu 64bit with KDE 4.8.4, kernel = 3.2.0-23-generic
This kernel should have force feedback support enabled, so no re-compiling is needed...
However, with my current wheel (Logitech Momo Racing Force black) I can't get FF working.
It is calibrated correctly in System Settings -> Input devices.

Some useful output perhaps...

**_inxi -Fc 0_**
```

System:    Kernel: 3.2.0-23-generic x86_64 (64 bit) Desktop: KDE 4.8.4
Machine:   Mobo: ASRock model: 870 Extreme3 R2.0 Bios: American Megatrends version: P1.80 date: 12/06/2011
CPU:       Quad core AMD FX-4100 (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) 
           Clock Speeds: 1: 1400.00 MHz 2: 1400.00 MHz 3: 1400.00 MHz 4: 1400.00 MHz
Graphics:  Card: NVIDIA G92 [GeForce 8800 GT] 
           X.Org: 1.11.3 drivers: nvidia (unloaded: nouveau,vesa,fbdev) Resolution: 1920x1080@50.0hz 
           GLX Renderer: GeForce 8800 GT/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 295.40
Audio:     Card: Creative Labs SB Audigy driver: snd_emu10k1 Sound: ALSA ver: 1.0.24
...

```

**_lsusb_**
```

Bus 004 Device 006: ID 046d:ca03 Logitech, Inc. MOMO Racing

```

**_cat /proc/bus/input/devices_**
```

I: Bus=0003 Vendor=046d Product=ca03 Version=0100
N: Name="Logitech  Logitech MOMO Racing "
P: Phys=usb-0000:00:12.0-5/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input7
U: Uniq=
H: Handlers=event6 js0 
B: PROP=0
B: EV=20001b
B: KEY=3ff00000000 0 0 0 0
B: ABS=3
B: MSC=10
B: FF=300040000 0

```

**_evtest_**
```

evtest /dev/input/event6

Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x46d product 0xca03 version 0x100
Input device name: "Logitech  Logitech MOMO Racing "
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 288 (BTN_TRIGGER)
    Event code 289 (BTN_THUMB)
    Event code 290 (BTN_THUMB2)
    Event code 291 (BTN_TOP)
    Event code 292 (BTN_TOP2)
    Event code 293 (BTN_PINKIE)
    Event code 294 (BTN_BASE)
    Event code 295 (BTN_BASE2)
    Event code 296 (BTN_BASE3)
    Event code 297 (BTN_BASE4)
  Event type 3 (EV_ABS)
    Event code 0 (ABS_X)
      Value      0
      Min        0
      Max     1023
      Fuzz       3
      Flat      63
    Event code 1 (ABS_Y)
      Value      0
      Min        0
      Max      255
      Flat      15
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 21 (EV_FF)
    Event code 82 (FF_CONSTANT)
    Event code 96 (FF_GAIN)
    Event code 97 (FF_AUTOCENTER)
Testing ... (interrupt to exit)
Event: time 1347096390.387372, type 3 (EV_ABS), code 0 (ABS_X), value 873
Event: time 1347096390.387410, type 3 (EV_ABS), code 1 (ABS_Y), value 127
Event: time 1347096390.387421, -------------- SYN_REPORT ------------
Event: time 1347096390.395302, type 3 (EV_ABS), code 0 (ABS_X), value 492
Event: time 1347096390.395350, -------------- SYN_REPORT ------------

```
=> Turning the wheel, pressing buttons gives a lot of output so seems to work.

**_fftest_**
```

fftest -d /dev/input/event6

Force feedback test program.
HOLD FIRMLY YOUR WHEEL OR JOYSTICK TO PREVENT DAMAGES

Device /dev/input/event6 opened
Axes query: 
Effects: Constant 
Number of simultaneous effects: 16
Upload effects[0]: Invalid argument
Upload effects[2]: Invalid argument
Upload effects[3]: Invalid argument
Upload effects[4]: Invalid argument
Upload effects[5]: Invalid argument
Enter effect number, -1 to exit
1
Now Playing: Constant Force
Enter effect number, -1 to exit
-1
No such effect

```
=> if I choose no. 1 (constant effect) the wheel only slowly moves to the left and stays there when it reached its maximum.
All other numbers have no effect, which comes as no surprise seeing the 'Invalid argument' messages.

I tried rFactor & Grand Prix Legends, both have FF enabled in config, wheel is recognized and 'works' but no FF.

---

