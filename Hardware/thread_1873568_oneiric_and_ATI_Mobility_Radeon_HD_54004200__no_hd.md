---
title: "oneiric and ATI Mobility Radeon HD 5400/4200 : no hdmi out"
date: 2011-11-01
forum: Hardware
---

### Post by magowiz82 on 2011-11-01
Hi,
I have these cards on my laptop:
```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series] (rev ff)

```but hdmi out doesn't work, the tv says "no signal"; with windows 7 it works out of the box.

I installed flgrx provided by official repo and I also tried to install a more recent version using the .run file provided by AMD, the hdmi monitor (tv) isn't listed in monitor settings and neither in catalyst control center.

xrandr gives the following :
```
 xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1600 x 1600
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1280x600       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   640x480        60.0 +
CRT1 disconnected (normal left inverted right x axis y axis)

```as you can see it lists only modes for internal monitor and CRT1 which is (I think) the display of VGA out.

Any hope to get hdmi video out working ?

---

### Post by Redblade20XX on 2011-11-02
Here take a look at this: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)

- Red

---

### Post by magowiz82 on 2011-11-02
I tried the sections : 
**X2/Dual GPU Cards and Dual/Multi Monitors **

but no luck.... nothing changes

---

