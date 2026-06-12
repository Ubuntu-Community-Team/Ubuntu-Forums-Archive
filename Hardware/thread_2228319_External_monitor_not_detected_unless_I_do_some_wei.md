---
title: "External monitor not detected unless I do some weird steps"
date: 2014-06-06
forum: Hardware
---

### Post by Jordananders on 2014-06-06
I have an intel laptop with integrated graphics (no graphics card). It has an hdmi port that I would like to use for my 22” monitor, but I am encountering an odd problem. The monitor is DVI, so I use an HDMI to DVI converter. 

Here is the problem. When I plug in the 22” monitor, and press fn + f8 (monitor switcher), the screen is not recognized. I also have a 20” monitor of the same brand (Planar) that I tested the setup with. For some reason, it worked with the 20”, but not the 22”. I then figured out that I can get the 22” monitor to work if I do the following:

-Plug in 20” monitor
-Switch display to the 20” monitor
-Unplug the 20” monitor
-Plug in the 22” monitor
-the larger monitor magically works

If I restart the computer, the computer SOMETIMES goes back to not recognizing the monitor. So every time I restart my computer, I need to grab the smaller monitors which belongs to my relative, and do the procedure above. Its very annoying. 

I thought of a possible solution, but I do not know how to go about doing it. Maybe I could set the large monitor up, and export some type of config file that the computer is forced to use on startup? IDK. Please help.

---

### Post by Jordananders on 2014-06-06
by the way I tried using the adapter with my chromebook, and it works with the smaller monitor. With the bigger monitor, it says it is not supported. But this does not explain why those series of steps make the monitor compatible under ubuntu.

---

### Post by tgalati4 on 2014-06-07
It could be a timing issue.  The DVI-to-HDMI converter prevents proper communication between the monitor and the graphics card.  Try it with an HDMI TV and see if it works consistently.  Then try buying a few DVI-to-HDMI converters (different brands with a return policy) and see if you get the behavior with each brand of converter.

The old-school way of handling this is to modify /etc/X11/xorg.conf and define a second screen with a fixed resolution.  Open a terminal and put in your resolution:

```
gtf 1920 1080 60
```

Cut and paste the modeline into the appropriate spot in xorg.conf.  Some reading:  [https://help.ubuntu.com/community/NvidiaResolutionXorgConf](https://help.ubuntu.com/community/NvidiaResolutionXorgConf)

By hardcoding the resolution, you can bypass the auto-resolution detection and possibly fix the detection problem.

---

### Post by Jordananders on 2014-06-09
Thank you. An HDMI TV works fine.

So do I need to modify these numbers before putting it into the xorg conf?

gtf 1920 1080 60

---

