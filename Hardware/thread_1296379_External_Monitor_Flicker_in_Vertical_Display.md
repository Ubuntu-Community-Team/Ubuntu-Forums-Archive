---
title: "External Monitor Flicker in Vertical Display"
date: 2009-10-20
forum: Hardware
---

### Post by ddygu on 2009-10-20
Hello, 

I recently started using my Samsung 204T as an external monitor for my laptop. I have it connected with VGA, and I setup my xorg.conf to fit both resolutions in virtual resolution (1680x1050 for laptop and 1600x1200 for external, giving 3280x2250 virtual). I also use this command:

```
xrandr --output LVDS --mode 1680x1050 --output VGA --rotate left --mode 1600x1200
```

to use my external in the vertical position. It works fine until about 10 or 15 minutes in the vertical mode. The external monitor starts displaying flickering scan lines. Returning to horizontal mode and turning the monitor off/on stops the flickering. 

I have turned off compiz, and use metacity, but the problem still persists. Any ideas as to what might be happening? I have an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller card. 


Thanks, 

-Greg

---

### Post by Chris_82 on 2009-12-19
I have a similar problem: When turning the laptop's LCD off, thus only being on the external monitor via VGA, there are funny lines bundled together distorting the vertical lines in only these regions in a snake-like way.

I am using Karmic..and I didn't touch xorg.conf.

[here is a Screenshot]("http://i50.tinypic.com/2vjc1l4.jpg")

cheers.

---

### Post by zoghimas on 2010-05-26
Apparently, this is an electrical problem and it has to do with the power circuitry (I guess you can't even call it a hardware problem): there is a website that explains what's going on [http://mrgnome.wordpress.com/2009/06/12/external-monitor-flicker-laptop-ground-loop-problem-solved/](http://mrgnome.wordpress.com/2009/06/12/external-monitor-flicker-laptop-ground-loop-problem-solved/)

If you're like me and the flickering stops once you stop charging your laptop, then this'll tell you what to do.

---

