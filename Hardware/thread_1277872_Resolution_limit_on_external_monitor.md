---
title: "Resolution limit on external monitor"
date: 2009-09-28
forum: Hardware
---

### Post by rg2530 on 2009-09-28
I have two Lenovo laptops - X60 and X61 - that I use with a BenQ T221W monitor.

Both laptops have a 1024x768 panel.  When I was running 8.04, the resolution of the external monitor (1680x1050) was detected and was used by default.  The internal panel would then only show the top left 1024x768 of the full display.

I recently upgraded to 9.04 and can't get the external monitor to correctly show any resolution above 1024x768.

For the X61:

```

$ lspci | egrep "VGA|Display"
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1680 x 1680
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0 +
   1600x1000      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 246mm x 185mm
   1024x768       50.0 +   85.0*    75.0     70.1     60.0     40.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1

```

I tried 8.10 on the X60 and it also defaults to 1024x768 so the behaviour must have changed between 8.04 and 8.10.

How can I get the 8.04 behaviour back?

---

### Post by tgalati4 on 2009-09-28
Yes, but you have to downgrade to 8.04.  There were major changes to xorg (and some regressions with Intel chipsets).

If you don't want to downgrade, then wait for Koala in a few weeks and see if that works.

---

### Post by rg2530 on 2009-09-28
Just found [http://ubuntuforums.org/showthread.php?t=1233897](http://ubuntuforums.org/showthread.php?t=1233897) and tried:
> 
$ xrandr --output LVDS --auto --output VGA --mode 1680x1050 --same-as LVDS

And I got the old behaviour.  The LCD is showing only the top 1024x768 of the whole 1680x1050 screen.

I wonder if it is possible to get this behaviour by default.  Note that I don't really want to force things in the xorg.conf file as I often travel with this laptop and won't have access to the external monitor.

I will try Koala when it is released.

---

### Post by Rehd on 2009-11-11
> **rg2530 said:**
> Just found [http://ubuntuforums.org/showthread.php?t=1233897](http://ubuntuforums.org/showthread.php?t=1233897) and tried:

And I got the old behaviour.  The LCD is showing only the top 1024x768 of the whole 1680x1050 screen.

I wonder if it is possible to get this behaviour by default.  Note that I don't really want to force things in the xorg.conf file as I often travel with this laptop and won't have access to the external monitor.

I will try Koala when it is released.

The problem persisted with my X61s and Koala.

I also used the xrandr solution (used an example form the man page). Both monitors (internal and external) where detected correctly, just that the settings of the internal monitor were used on both...

The solution for me was
```
xrandr --output VGA --auto --above LVDS
```
since the optimal settings for VGA were detected (as in your case, too) it might be sufficient just stating "--auto". I found "--above" useful, which extends the desktop and sets the external monitor "above" my laptop display.... it is also possible to state "--right-of"...

In essence and in reply to your problem with multiple situations in which the external montior has to be configured:
```
xrandr --output VGA --auto
```
should do the job anytime...

---

