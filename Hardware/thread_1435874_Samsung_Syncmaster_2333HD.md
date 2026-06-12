---
title: "Samsung Syncmaster 2333HD"
date: 2010-03-22
forum: Hardware
---

### Post by xaenn on 2010-03-22
Hi all,

I just recently purchased a Samsung Syncmaster 2333HD, but unfortunately I'm having some problems getting it working with Ubuntu (I have a dual boot with Windows XP, and it is working fine there). The problem is I can't get the monitor to display at the correct resolution (tried this with Ubuntu 9.10, then updated to 10.4 beta with no improvement). Right now it is only letting me display at 640x480 or 320x240 (these are the only options available in the nvidia display settings manager). I have the current version of the nvidia proprietary drivers installed, but I have also used the opensource nv driver without any better luck. Here is the graphics card that I'm using (built into the motherboard):

```

 $ lspci -v 
# 00:05.0 VGA compatible controller: nVidia Corporation  C51G [GeForce 6100] (rev a2)

```I tried manually setting the resolution in the display section of xorg.conf, but those settings are seeming to get completely ignored (I can post xorg.conf if there really is a need, but my Ubuntu machine is running at snail pace right now, so I am trying to avoid using it right now if possible).

I also tried to use xrandr to manually set the resolution, but it was to no avail. Here are the relevant commands and output:

```

$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT  2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz Modeline "1920x1080_60.00"  173.00 1920 2048 2248 2576   1080 1083 1088 1120 -hsync +vsync

$ xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576    1080 1083 1088 1120  -hsync +vsync

$ xrandr --output default --mode 1920x1080_60.00
xrandr:  screen cannot be larger than 640x480 (desired size 1920x1080) 

$  xrandr
Screen 0: minimum 320 x 240, current 640 x 480, maximum 1920 x  1080
default connected 640x480+0+0 0mm x 0mm
    640x480    50.0*
     320x240    51.0
    1920x1080_60.00    60.0

$ xrandr --output  default --mode 1920x1080_60.00
xrandr: Configure crtc 0 failed

```I will be really grateful for any help that anyone can offer. If any more information about my system is required, please let me know and I'll be happy to provide it.

Thank you,
-Daniel

---

### Post by xaenn on 2010-03-23
bump. Anyone?

---

### Post by myislanduniverse on 2010-04-10
I've been trying to do the same thing; I copied what you did verbatim, with the exception that I set it specific to the output, rather than trying to default it, so I'm not sure if it'll apply to you.

```
~$ xrandr --output VGA1 --mode 1920x1080_60.00
```

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) outlines using xrandr, and some options for making the changes persistent.

---

### Post by myislanduniverse on 2010-04-10
Take it back, I also had to ...

```
$ xrandr --addmode VGA1 1920x1080_60.00
```

Before I could set the output to that mode.


Edit:  Added the 3 lines (the --newmode, --addmode, and --output commands) to /etc/gdm/Init/Default and it reboots into the right res).

---

