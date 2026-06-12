---
title: "Latest Gutsy Broke My Dual Screen Display"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by gers4302 on 2007-09-19
I'm running Gutsy on an Dell Inspiron 600m with a 17" Dell LCD attached to it.  The Inspiron LCD runs at 1400x1050 and the Dell LCD runs at 1280x1024.

I had a xorg.conf that worked well enough in Feisty that gave me access to both monitors in a non-rectangular fashion.

I upgraded to Gutsy and everything worked well, until today (as is the nature of development).

Right now, I can only get mirrored display.  xrandr gives me the following output:

```
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 2048 x 1200
VGA-0 disconnected (normal left inverted right)
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected 1400x1050+0+0 (normal left inverted right) 0mm x 0mm
   1400x1050      60.0*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9 
```

The concerning line is the 'maximum 2048x1200' line, which seems to make me unable to set up a merged screen.  If I attempt to run 'xrandr --output LVDS --left-of DVI-0', I get:

```
xrandr: screen cannot be larger than 2048x1200 (desired size 2680x1050)
```

What should I do to fix this?

---

### Post by gers4302 on 2007-09-19
Quick addition...

If I do the following, then I can get the desired setup at a lower resolution.

```
$ xrandr --output DVI-0 --mode 1024x768
$ xrandr --output LVDS --mode 1024x768
$ xrandr --output DVI-0 --left-of LVDS
```

So it seems that xrandr either doesn't support non-rectangular setups, or I'm doing something wrong (which is most likely the case).

---

