---
title: "Monitor becomes black when attempt to resize window when screen is rotated"
date: 2015-06-01
forum: Hardware
---

### Post by dgtorpedo on 2015-06-01
Hi,
when I try to resize a window when the screen is rotated (Settings Manager > Display > Rotation) the monitor becomes black and I need to restart with Alt+Stamp+B.
More precisely, it becomes black when:
* the window is resized manually
* it is resized over a certain dimension

I use Xface with xubuntu 14.04

What could I check?
Thanks

Edit:
Some usefull information:
I've got a Lifebook T4220 with:
graphic card
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

```

driver
```

sudo lshw -c display | grep driver
       configuration: driver=i915 latency=0

```

and
```

xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 32767 x 32767
LVDS1 connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      60.0*+   60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by dgtorpedo on 2015-06-02
Looking for a solution in the Fujitsu's manual, under the section *troubleshooting*, in *video problems*, I've found this:
[TABLE="width: 500, align: left"]
[TR]
[TD]Problem[/TD]
[TD]Possible cause[/TD]
[TD]Possible solutions[/TD]
[/TR]
[TR]
[TD]The application display
uses only a portion of your
screen and is surrounded
by a dark frame.[/TD]
[TD]You are running an application
that does not support 800 x
600/1024 x 768 pixel resolution
display and display compres-
sion is enabled.[/TD]
[TD]When compensation is disabled, a clearer but
smaller display for applications that do not support
800 x 600/1024 x 768 pixel resolution will result. You
can fill the screen but have less resolution by
changing your compensation setting. (See the Video
Features submenu, located within the Advanced
menu of the BIOS. See “BIOS Setup Utility” on
page 39.[/TD]
[/TR]
[/TABLE]
Unfortunately, when I bought this pc from ebay I discovered that someone has locked the bios with a password, so I can't investigate further.

So, the 1400x1050 resolution is well supported with screen in normal mode (xrandr -o normal) or inverted (xrandr -o inverted) but the [SXGA+]("http://en.wikipedia.org/wiki/Graphics_display_resolution#SXGA.2B_.281400x1050.29") is not supported in left or right mode.

A possible solution is to downgrade to a 1024x768 resolution only when I turn the screen at left or right.

---

### Post by dgtorpedo on 2015-06-02
Here the trick (from [FONT=courier new]man xrandr[/FONT]).

When I turn the screen at left (or right):
```
xrandr -o left
```

I change the resolution from 1400x1050 to 1024x768 (because it is supported, see my previous post)
```
xrandr -s 1024x768
```

then the trick:
```
xrandr --fb 1400x1050 --output LVDS1 --scale-from 1024x768
```

That is, I fitt the 1024x768 in the 1400x1050.

---

