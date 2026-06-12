---
title: "Automatically enable/disable external monitor when connected to a laptop?"
date: 2010-11-06
forum: Hardware
---

### Post by hydravien on 2010-11-06
Hi all, 
*
I've got an HP touchsmart TX2 that I use as my primary computer, but when I'm at home I usually have it hooked up to an external monitor through a docking station. The laptop has an ATI 3200 chip in it. 

So I managed to configure both monitors to work the way I want (my external lcd running at 1920*1080 and laptop at 1280*800) and it works great. 
The problem I'm having is that I often disconnect the laptop from the docking station to go to school/work some place else. When I do this in Win7, the displays automatically reconfigure and move everything to my laptop screen. 
In ubuntu (10.04), when I disconnect, it doesnt detect the missing monitor and leaves everything where it was, meaning my task bars are still on the now non existent monitor, and I can't it back without plugging back in and moving everythign over manually, then disabling the external lcd. 
Similarly, when i want to plug it back in, i have to go through the reverse process. 
So my question is, is there a way to automatically move all the windows and task bars over when the monitor is disconnected?

Thanks in advance
Nick

---

### Post by uriel1998 on 2010-11-30
I don't know about *automagically*, but you could bind a key (or create a launcher for Launchy/Gnome-Do) that resets the resolution for the behavior you want.  (I do this for fullscreen apps that are naughty and change resolutions.)

This will reset your resolution
```
xrandr -s 0
```

This will attempt to enable all attached outputs
```
xrandr --auto
```

You can also look at this rather lengthy (and somewhat dated when it refers to Ubuntu) guide for using xrandr:  [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2).  

As far as traveling goes, the Fn-F7 solution works the same for me for Ubuntu 10.04 as it did with Vista.

---

### Post by makos81 on 2011-07-09
Hi!

The same usability issue here on my old BenQ R56 notebook with nVidia GeForce 8400M.
When I disconnect the external monitor - it is not disabled in Ubuntu.

xrandr -s 0 does nothing
xrandr --auto thowing "xrandr: Failed to get size of gamma for output default"

Thanks!

---

### Post by uriel1998 on 2011-07-12
> **makos81 said:**
> Hi!

The same usability issue here on my old BenQ R56 notebook with nVidia GeForce 8400M.
When I disconnect the external monitor - it is not disabled in Ubuntu.

xrandr -s 0 does nothing
xrandr --auto thowing "xrandr: Failed to get size of gamma for output default"

Thanks!

What version of Ubuntu are you running?  It's possible things changed… I run 10.04

---

### Post by realzippy on 2011-07-12
..have a look at [disper]("http://willem.engen.nl/projects/disper/").

---

### Post by MikeFranklet on 2011-10-23
Beauty! xrandr --auto works like a charm. Set a keyboard shortcut and it's perfect. I just wish it would autodetect like 11.xx, but I'll take stability over convenience any day. Thanks for posting this solution!

---

### Post by uriel1998 on 2011-10-23
You may want to take a look at this script I made that is a bit more advanced.  Not only does it detect for the attached VGA monitor, but it also checks to see if there's HDMI attached and, if so, reroutes pulseaudio to HDMI out through the **pacmd** utility.

[http://pastebin.com/Z4bZfiU4](http://pastebin.com/Z4bZfiU4)

---

### Post by cmeiklejohn on 2011-11-15
> **MikeFranklet said:**
> Beauty! xrandr --auto works like a charm. Set a keyboard shortcut and it's perfect. I just wish it would autodetect like 11.xx, but I'll take stability over convenience any day. Thanks for posting this solution!

Auto-detection works in 11.xx Ubuntu or did you need to do something with xrandr?

---

