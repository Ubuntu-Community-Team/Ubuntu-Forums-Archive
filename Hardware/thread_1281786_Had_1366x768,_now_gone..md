---
title: "Had 1366x768, now gone."
date: 2009-10-03
forum: Hardware
---

### Post by Meneldir on 2009-10-03
Hi, I'm having a little problem, and I couldn't find the answer in other post I've read.

I have an Acer Laptop with an ATI Radeon HD 3200 on-board graphic card.

The best resolution for the notebook is 1366x768, since any other looks blured.

The issue:
I've connected an external monitor to the VGA output and worked fine. After that, I've disconnected the monitor and continued working with my nice 1366x768 resolution.
After I re-restarted the laptop, it started with a 1280x720 resolution, blured.
I don't have now the option to change it back from System > Preferences > Display.

When I run xrandr I get:
```
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 1280 x 1792
LVDS connected 1280x720+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1280x720       59.9* 
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

```

I've tried first with:
[FONT="Courier New"]xrandr --fb 1366x768 --output LVDS --auto[/FONT]
but I got:
[FONT="Courier New"]xrandr: screen cannot be larger than 1280x1792 (desired size 1366x768 )[/FONT]

and the I tried:
[FONT="Courier New"]xrandr --addmode LVDS 1366x768[/FONT]
but I got:
[FONT="Courier New"]xrandr: cannot find mode "1366x768"[/FONT]

I'm using the Ubuntu video drivers (not ATI Catalyst), but I've installed ATI's and it didn't show the 1366x768 option either.

anyone knows what I can do to get back 1366x768?

------------------------------------------------------------------
My solution, maybe not the best, but worked for now:
I've connected the VGA monitor to the external output again, and I'm using it that way... joke joke.. It's true that I've connected it again, but I've started changing modes with the monitor plugged until a pop of adjusting the virtual size automatically or something like that appeared (it said it was recommended to do so, and also when I connected it the first time the pop up appeared). Done that, then logged out and in and the 1366x768 mode was back. Now I'm happy and I can continue using the laptop without losing my eyes.

Moral: &#12364;&#12435;&#12400;&#12390;

---

### Post by betolima on 2009-10-03
Hi, 

If you really can run your monitor on that resolution, you must change the buffer size.

Your problem sits on this line:

"...x 720,** maximum 1280 x 1792**" .. 

My problem started to be solved on this site:
[http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux](http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux)

I did a small search over here but didn't find how I changed that maximum... it took me several weeks before I find it.. but try to mess around with your video buffer size ...

When I find something else I  post here ...

---

