---
title: "Resolution NVIDIA GEFORCE GT 560M"
date: 2013-06-18
forum: Hardware
---

### Post by unclearimage on 2013-06-18
Trying to get to a good resolution tried xrandr as tutorials online suggested, trying to get 1366x768 as the manufacturer suggested. Was running 1920x768 or something on windows. My TV is refered to as HDMI-0. Did the XRANDR this is what I got.



jonesy@IBuyPowerLP:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync


jonesy@IBuyPowerLP:~$ xrandr --addmode HDMI-0 "1600x900_60.00"


X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34


Dunno why it won't work, also tried this resolution 1600x900 because that's what the guide had so I just used that.

---

### Post by papibe on 2013-06-18
Hi unclearimage.

Could you post the result of these commands?
```
xrandr -q

xvidtune -show

nvidia-settings -q CurrentMetaMode
```
Regards.

---

### Post by unclearimage on 2013-06-18
xrandr -q
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080      59.9*+   39.9  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 640mm x 360mm
   1920x1080      25.0*+   30.0     30.0  
   1280x720       60.0     59.9     50.0  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0     25.0  
   720x480        59.9     59.9     30.0  
   640x480        59.9     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0x359)  118.2MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   56.0KHz
        v: height  900 start  903 end  908 total  934           clock   59.9Hz


xvidtune -show
"1920x1080"   139.50   1920 1968 2000 2096   1080 1083 1088 1111 -hsync -vsync



nvidia-settings -q CurrentMetaMode
  Attribute 'CurrentMetaMode' (IBuyPowerLP:0.0): id=50, switchable=yes,
  source=RandR :: DPY-1: nvidia-auto-select @1920x1080 +0+0
  {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, DPY-2: nvidia-auto-select
  @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}

---

### Post by papibe on 2013-06-18
Thanks.

I don't see '1366x768' listed as a supported resolution. I wouldn't try to set it.

I see that 1280x720 is available, and it should be close to what you want. Try setting it up using 'Nvidia X Server Settings'.

Let us know how it goes.
Regards.

---

### Post by unclearimage on 2013-06-18
sorry got back on windows I'm looking for 1768x992 the 1280x720 cuts off 4 inches on the right side.

---

### Post by papibe on 2013-06-18
> **unclearimage said:**
> ..cuts off 4 inches on the right side.
That looks like an [Overscan]("http://en.wikipedia.org/wiki/Overscan") problem. In other words, a setting on the TV itself not in the computer.

In my Sony Bravia the settings is under the screen menu, the value "Full Pixel". In my brother's Samsung is something like Picture Options -> Screen Size ->  P.size to 'Full Scan'.

Let us know how it goes.
Regards.

---

### Post by unclearimage on 2013-06-18
It's not my T.V. I've already checked and tried all that. 
Forget it, tried Zorin 9 months ago same ****, spent forever trying to get basic crap working, been spending every minute since I installed last night trying to get stuff working that's instant with windows, I'm going back to windows 8. 
Thanks for your help, but Linux not worth this much of a headache.

---

