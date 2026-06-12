---
title: "Beamer on Intel GMA 4500"
date: 2009-05-26
forum: Hardware
---

### Post by RikoW on 2009-05-26
Dear all,

I have a Dell Lat E4300 with Jaunty installed. The laptop has the above graphics chip. Most things seem to work fine: hibernate/suspend, full 1280x800 resolution, decent compiz performance. However, today I tried to attach a beamer to the laptop for presentation purposes, but didn't get a signal on the beamer.

On my previous laptop (Lat D600 with Ubuntu 8.04) I just used xrandr to clone the display to the external beamer. Doing the same only gives me a black screen. Also fiddling with grandr or System -> Preferences -> Display did not help.

The beamer seems to be recognized. This is what xrand tells:

```
> xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       60.0*+   40.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

Now I connect the beamer

```

> xrandr --auto --output VGA --mode 1024x768 --same-as LVDS
> xrandr 
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2640 x 800
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       60.0*+   40.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

Something is happening on the beamer, though, because it goes from showing the makers information and "no input detected" to black.

Any ideas?

Thanks and cheers,

                Riko

---

### Post by RikoW on 2009-05-27
Hi all,

one step forward: it seems to work with the -386 kernel instead of the default -generic one (what is the difference?)

However, to get the entire presentation on the projector, I also have to reduce the size of the LCD screen to a 4:3 format (as supposed to native 16:10).

Not very convenient, but a reasonable work-around.

Cheers,
           Riko

---

