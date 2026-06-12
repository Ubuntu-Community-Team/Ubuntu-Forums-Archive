---
title: "xrandr does not accept 2560x1440 resolution with nvidia-352"
date: 2015-12-24
forum: Hardware
---

### Post by johannes-mittendorfer on 2015-12-24
I tried using the full resolution of a new computer monitor which supports 2560x1440 at 60Hz. However, the graphics card won't let me set the resolution higher than 1920x1080. I installed the nvidia-352 restricted driver and also tried to change the resolution in nvidia-settings. But as I had success with a different computer and the same monitor I also tried it with xrandr:

The output of 

```
[FONT=courier new]cvt 2560 1440[/FONT]
```

is

```
# 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
Modeline "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
```

Next I tried to add it as a new mode:

```
xrandr --newmode "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
```

It worked but the assignment to the port with the following command

```
xrandr --addmode HDMI-0 "2560x1440_60.00"
```

failed:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30
```

I'm using a HDMI-1.4 cable and the specification of the graphics cards (GeForce GT 705) says resolutions up to 2560x1600 are supported. By using nouveau I managed to get 2560x1440 but it looked ugly and I also need the nvidia driver for some applications. Sadly the computer does not have a display port.

Any ideas on how to get the full resolution?

---

