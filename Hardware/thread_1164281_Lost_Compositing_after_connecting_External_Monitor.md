---
title: "Lost Compositing after connecting External Monitor"
date: 2009-05-19
forum: Hardware
---

### Post by HeirPixel on 2009-05-19
Strangely enough, today was actually the first time I connected an external display to my laptop. After connecting the monitor and setting it to extend my current desktop, a dialog box popped up telling me I would have to write some change to some setting file and restart my system for changes to take effect.

Now I've lost my compositing!! Yes, I *know* I should have paid more attention to the message, but now I have absolutely no idea what file was modified and how.

Here's a copy of output from **sudo lshw -C display** :
```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```
Any ideas.......?

---

### Post by HeirPixel on 2009-05-19
I've also lost the ability to play video files. Both VLC and Totem close immediately. Yikes!

---

### Post by HeirPixel on 2009-05-21
[bump]
Any ideas on this one...?

---

### Post by joslinar on 2009-05-21
This just happened to me right now, yikes. I guess the display configuration changed the driver. Need Help.

---

### Post by joslinar on 2009-05-21
I went to:
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)
and when I tried method 2 Xorg asked me to reconfigure the display. I selected the "create a new configuration" or something like that option it solved the problem.

In the xorg.conf file i found the following
```
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
```

maybe the recomendation to run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
is what is takes.

---

### Post by HeirPixel on 2009-05-21
Ah, brilliant! I was seriously hating life over losing what I would have thought was such a meaningless "eye-candy" feature.

---

### Post by roystreet on 2009-08-03
Hi - Everything worked until I tried putting my resolution up to the levels I had them before.  My resolutions are: External is 1920x1080 & the other one is 1280x800.

I tried various monitor resolutions and it worked until I brought them up to a higher level.  Now get this, if I boot my laptop without the monitor plugged in, then it works perfectly.  I get all of the eye candy & the high resolution.  I know it has something to do with that 2nd monitor.  Any ideas?

Thanks!

~roystreet

---

### Post by roystreet on 2009-08-24
Hello,
   A couple weeks ago I asked this question & I didn't know if anyone had any experience or thoughts on how to fix this?  As soon as I log in with my external monitor plugged in, it states that comp-fusion wasn't able to work right.

Thanks,
~roystreet

---

### Post by HeirPixel on 2009-08-24
> **roystreet said:**
> I tried various monitor resolutions and it worked until I brought them up to a higher level.  Now get this, if I boot my laptop without the monitor plugged in, then it works perfectly.  I get all of the eye candy & the high resolution.  I know it has something to do with that 2nd monitor.  Any ideas?
My guess is that it's your display driver moreso than the monitor itself. If the driver isn't recognising the full capabilities of the monitor (which happens just as often on Windoze) then it will fail when you try to force it to a higher resolution.

Since you're on a laptop you could take it to another monitor and try there. See what you get and come back to let us know your results.

---

### Post by roystreet on 2009-08-24
I will say this - That I believe I had this at a much lower resolution on my external monitor & it worked correctly.  My external monitor has quite a bit larger resolution though.

~roystreet

---

### Post by roystreet on 2009-08-25
Hi - I don't know how this will affect anything, but in the compiz manager it doesn't have my resolution listed.  Mine once again is 1920x1680.  It doesn't go that high.  Could this be the root of the matter?  I tested it by adding a line in there for a higher resolution, but it had no affect.

I wanted to clarify concerning the msg that shows up when I log in.  Avant is trying to start when I log in & the msg tells me that compiz(-fusion) isn't started.  I believe that's how it goes.

Thanks!
~roystreet

---

### Post by Yellow Pasque on 2009-08-25
If you're running an extended desktop at a resolution larger than 2048x2048, then direct rendering (and thus, compiz) won't work. [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146859](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146859)

---

### Post by roystreet on 2009-08-25
Right...But I'm not using a resolution higher.

Or is it adding the total of them both?

---

### Post by roystreet on 2009-08-25
OK, OK I read the threads from that link you sent me.  It mentions something that "may" work & appears to have worked for others.  Someone there mentions they stack their monitors vertically?  Is there a setting or something where I tell it to stack them vertically?

Thanks,
~roystreet

---

### Post by Yellow Pasque on 2009-08-25
Maybe a command like the following?
```
xrandr --output VGA --auto --below LVDS
```

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things)

---

### Post by roystreet on 2009-08-25
> **Temüjin said:**
> Maybe a command like the following?
```
xrandr --output VGA --auto --below LVDS
```

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things)

So I simply could drop that command in without any changes to it & it may work? Or do I need to modify it some?

Thanks

---

### Post by Yellow Pasque on 2009-08-25
What is the output of this?:
```
xrandr -q
```

---

### Post by roystreet on 2009-08-25
Just a quick FYI - I can't test this until I get home

---

### Post by roystreet on 2009-08-26
**Result:**
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 3200 x 1080
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)

```

Here is the result.  I obviously don't have the external monitor connected to my laptop, so I don't know if that's why it doesn't show the 1920x1680.  I couldn't bring my monitor with me today.

I'm starting to put together in my mind that if I set my monitors to mirror instead of extended & then close my laptop screen that my (Big) external monitor will be able to have those effects?  Do you think this would work?
Also, I would imagine that there is some way to make the extended settings work since (Only my imagination here) Aero works great on both in Vista. 

Thanks!
~roystreet

---

### Post by roystreet on 2009-08-27
OK - I've been able to do it while the monitor is plugged in:
```

Screen 0: minimum 320 x 200, current 2944 x 1080, maximum 3200 x 1080
VGA connected 1920x1080+0+0 (normal left inverted right x axis y axis) 520mm x 290mm
   1920x1080      60.0*+   60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1024x768+1920+312 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  

```

There is a lot more information than the first one for sure.  I'm starting to understand it better also.

*Obviously I was wrong with what I thought it was.  It is 1920x1080, not 1680.  

Thanks,
~roystreet

---

### Post by Yellow Pasque on 2009-08-27
> I'm starting to put together in my mind that if I set my monitors to mirror instead of extended & then close my laptop screen that my (Big) external monitor will be able to have those effects? Do you think this would work?
Yes.

---

### Post by roystreet on 2009-08-27
So what about the other thing you said?
> xrandr --output VGA --auto --below LVDS

Will that allow me to still use 2 monitors (extended) & still use compiz?  Is the concept that it use the available "realestate" beneath it since there is not enough left on the side?

Thanks,
~roystreet

---

### Post by Yellow Pasque on 2009-08-27
It should allow direct rendering in theory.

> Is the concept that it use the available "realestate" beneath it since there is not enough left on the side?
This picture illustrates it very well: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen)

---

### Post by roystreet on 2009-08-27
It appears that it is memory dependent - I have 4 gb of RAM, is that not enough?  To increase the virtual screen - or - am I looking at this wrong?

*Or...*Since mine is an intel chip am I limited?

Thanks,
~roystreet

---

### Post by spinvox on 2010-11-15
hi, i started using external monitor couple of days ago but then changed my laptop from hp compaq 6710b to nx7400 as that has a higher resolution built in to the laptop. I swapped the hard disk to the nx7400 (I installed on this one too about a month ago as with 6710b instalations have problems) Standalone the laptop works great but when i connect to the same external monitor my compositing used to stop working, Docky pointed this out, my screen rotation using compiz did not work, neither did videos on either screen. But when I reduced the resolution and logged out and in (or restart) it works fine now. But only on a max resolution for me 1152x864 on the laptop and 832 x 624 on the external monitor. Where as otherwise I can get both upto 1680 x 1050 they work together connected fine but then compositing stops and videos dont run. So solution is to try and reduce it to a level they both work fine. Maybe there is a max size on dual desktop that the graphics driver supports to run with compiz. thanks home this helps some one. and if anyone has a solution to work it max resolution do let the world know. thanks

---

