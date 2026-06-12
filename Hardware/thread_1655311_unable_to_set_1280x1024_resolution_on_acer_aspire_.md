---
title: "unable to set 1280x1024 resolution on acer aspire 5920"
date: 2010-12-29
forum: Hardware
---

### Post by vipanbalrai on 2010-12-29
Hi,

I wanted to set display resolution to 1280x1024 but ubuntu only display 1280x800 resolution. 1280x1024 resolution was supported on windows XP sp2. Can any one help me setting up resolution.

I am using ubuntu 10.10. I have tried the following:

I tried ddcprobe command it give me following output:
vbe: VESA 3.0 detected.
oem: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)GM965/PM965/GL960 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 8174
eisa: AUO8174
serial: 00000000
manufacture: 1 2006
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@60
monitorid: AUO
monitorid: B154EW08 V1

I tried to set resolution using xrandr

first i created modeline using cvt/gtf

then i added new mode using following command

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

after that it shows following output if i run xrandr -q command

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0xc8)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

but when i try to add mode then it gives me error

xrandr --addmode LVDS1 "1280x1024_60.00"

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

Please help me to set the resolution.

Thanks

---

### Post by Kirboosy on 2010-12-29
Has your computer had or prompted you to install hardware drivers?

---

### Post by pi/roman on 2010-12-29
Your LCD screen is only rated up to 1280x800 and that is widescreen so a standard resolution such as 1280x1024 would cause your screen to look stretched if it is possible.  I am hesitant to tell someone not to try something since linux is all about freedom to try what you want and if windows can do it why not linux.  You may be able to force it to 1280x1024 by a custom xorg.conf. Be prepared with a live cd in case you need to boot up with it and edit your xorg.conf if your computer won't display a screen properly after the changes.

**Aspire 5920 Series Specifications**
LCD Properties 15.4" WXGA high-brightness Acer CrystalBrite™ TFT LCD, 1280 x 800 pixel resolution

---

