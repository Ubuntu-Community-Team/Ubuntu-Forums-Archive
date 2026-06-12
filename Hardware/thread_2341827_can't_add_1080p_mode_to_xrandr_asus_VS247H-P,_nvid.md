---
title: "can't add 1080p mode to xrandr asus VS247H-P, nvidia"
date: 2016-11-01
forum: Hardware
---

### Post by austinj on 2016-11-01
My 1080p monitor is stuck at 1360x768 resolution in ubuntu 16.04. I've tried to add a new mode to xrandr but end with this error:
```
X Error of failed request:  BadMatch (invalid parameter attributes)  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  45
  Current serial number in output stream:  46

**SPECS**
Monitor: Asus VS247H-P
Cable: amazon basics hdmi
graphics card: gigabyte windforce gtx970
driver: nvidia-361 (have tried it with multiple nvidia drivers)


```

Here's the full method I'm trying.

```

 xrandr
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96*   59.80  
   1152x864      60.00  
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)



```

```
cvt 1920 1080# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync



```

```
[COLOR=#111111][FONT=Consolas]xrandr --newmode [/FONT][/COLOR]"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```

```
xrandr --addmode HDMI-0 "1920x1080_60.00"X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  45
  Current serial number in output stream:  46



```

I'm fairly new to ubuntu so I'm not sure which parameters are invalid. Also, if I get this to work how would I make it persist through startup?

---

### Post by him610 on 2016-11-01
You might have a better chance of setting your desired resolution by using Nvidia X Server Settings. You may have it already installed. If not, open Synaptic and search on "nvidia" (it will show as "nvidia-settings) then install it.

I have similar, but older, less capable gfxcard and monitor with max set at 1920x1080.

---

### Post by austinj on 2016-11-01
I forgot to mention I already tried that. Nvidia X server is showing the same options as xrandr. caps out at [COLOR=#000000]1360x768.[/COLOR]

---

### Post by him610 on 2016-11-01
If you have one, you could try replacing your HDMI cable with  a DVI cable.

This may or may not work for you... 
With your favorite editor, using *sudo*, open */etc/default/grub*
Find the line that begins,  > # GRUB_GFXMODE=640x480
Change it to read,  > GRUB_GFXMODE=9999x8888  where 9999x8888 is desired resolution(Note deleted crunch)

Carefully review your edits then save the file.
Next, from the command line,* sudo update-grub*
Reboot your computer. 
Hopefully, your monitor will display the desired resolution.

---

### Post by austinj on 2016-11-01
Unfortunately, I don't have a DVI cable handy. Though I'm seriously considering picking one up. I just tried editing grub but nothing seems to have happened. 

Thanks for your help so far.

---

### Post by austinj on 2016-11-03
bump, still haven't been able to find a solution for this.

---

