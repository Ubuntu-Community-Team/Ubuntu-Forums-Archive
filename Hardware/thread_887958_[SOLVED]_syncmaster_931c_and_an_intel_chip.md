---
title: "[SOLVED] syncmaster 931c and an intel chip"
date: 2008-08-12
forum: Hardware
---

### Post by kaurman on 2008-08-12
Hi!

I am using Samsung's 931c which is connected to my laptop. Everything would be nice, if it could give me a 1280x1024 resolution as it should. Unfortunately, after a fresh install, the best it can do is 1024x768.

There were times when all this could've been solved with 'sudo dpkg-reconfigure xserver-xorg' but since 8.04 it doesn't even ask me about video settings.

My current xorg.conf (relevant part):

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"i810"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

All I know is that I once actually had a xorg.conf which gave me 1280x1204 with the external monitor and when I disconnected it and restarted x, the laptop's screen showed its own correct resolution. At the moment the laptop is also showing 1024x768 (external monitor disconnected) but as it has a 12,1 inch screen, I am pretty sure that it's correct resolution is actually ?x800. I am not sure about the first half but if you are then please tell me. 

But that is not the main issue....

I am actually looking for a working part of xorg.conf which would solve my troubles. 

PS The chipset is something among the following: Mobile 945GM/GMS/GME, 943/940GML

Thanks in Advance,

K

---

### Post by ggaaron on 2008-08-12
First: don't use i810, it's the old driver, intel is the new developed one.

Put this in your xorg conf (change as needed):
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Default Monitor"
        Device          "Default Video Device"
        SubSection "Display"
                Virtual 1280 1280
        EndSubSection
EndSection

Virtual is max size of supported monitors.

From some time Xorg uses hal so things changed, like you noticed in dpkg-reconfigure. xorg.conf in not so important any more. Now your card should be detected and configured at X start. To manage screens new tool named xrandr is used. There are some guis for this, but if you are not afraid of terminals then I'd recommend using one as guis are bad and didn't work for me. Xrandr runs in already open X session, so log in, start terminal, call 'xrandr'. It will give you list of plugged monitors with their supported resolutions. Now use something like 'xrandr --output LVDS --off --output VGA --mode 1280x1024'. Better turn of compositing (compiz/KWin effects) before trying as they might hang. If it worked and you would like to have it all the time in xorg.conf then I'd search for the guide, there was one.

---

### Post by kaurman on 2008-08-13
Hi!

I changed Xorg's "Screen" section according to your post and replaced i810 with intel in the 'Device' section but it didn't seem to help.

Xrandr shows the following after x has been restarted with the new config:
```


Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       65.3*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```

All the best,

K

---

### Post by ggaaron on 2008-08-13
Similar problem with ati:
[https://bugs.freedesktop.org/show_bug.cgi?id=15648](https://bugs.freedesktop.org/show_bug.cgi?id=15648)
Look at the second post - there is how to add new resolutions (temporary for one session I think). Remember to change VGA-0 to VGA.

---

### Post by kaurman on 2008-08-13
Hi!

That works! A temporary solution but at least I dare to look at my monitor again.

Thanks.

K

---

### Post by ggaaron on 2008-08-13
Modelines can be added in xorg.conf like this:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        VendorName      "Sun"
        ModelName       "X7200A"
        Option          "DPMS"
        ModeLine        "1600x1200" 132.000 1600 1608 1672 1776 1200 1205 1215 1239 +hsync +vsync
EndSection

```
As for xrandr in xorg.conf:
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

---

### Post by kaurman on 2008-08-15
Hi!

Adding the necessary lines to xorg.conf made everything work automatically.
Thanks again.

K

---

