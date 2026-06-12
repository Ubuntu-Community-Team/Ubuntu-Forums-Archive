---
title: "Samsung 226BW @1680x1050 on Thinkpad x301"
date: 2009-11-15
forum: Hardware
---

### Post by JuddGarratt on 2009-11-15
I have an old Samsung 226BW that I would like to use as an external monitor from my Thinkpad x301 running Ubuntu Karmic.

When I connect the 226BW, it seems to work fine but I cannot choose the native 1680x1050 resolution in Display. Only lower resolutions are listed and these look wonky/blurry when selected.

Some Googling suggests changes to xorg.conf - however I do not have an xorg.conf.

I generated a new xorg.conf by dropping out of GDM and running
```
 Xorg -configure
```However, I can't seem to get X to start using this.

I'm quite new to Ubuntu so not sure what I should try next. Does anyone know how to get the 226BW working under **Karmic**?

---

### Post by JuddGarratt on 2009-11-17
Solved. In a way.

Got the Samsung 226BW working @ 1680x1050 (solution below).

However, the fix needs to be implemented on every boot and the screen exhibits blurry patches which makes reading text hard.

Net result: selling the Samsung and buying a new ViewSonic.

**Solution**

In case it helps anyone else, I've written out the solution below. Credit to [http://bbs.archlinux.org/viewtopic.php?pid=611851](http://bbs.archlinux.org/viewtopic.php?pid=611851) for the xrandr approach.

I'm not sure if this is technically the 'right' way to fix screen res issues, but it worked for me (albeit with blurry patches - you may have different mileage).

1. Run xrandr and write down the location of the external screen. For me it was VGA1:
```
$ xrandr
Screen 0: minimum 320 x 200, current 2592 x 900, maximum 8192 x 8192
VGA1 connected 1152x864+0+36 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 1440x900+1152+0 (normal left inverted right x axis y axis) 287mm x 180mm
   1440x900       60.0*+   59.9     50.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```2. Generate a modeline using gtf - for me this was:
```
$ gtf 1680 1050 60

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

```One thing to note here is that the modeline I got for my 226BW is vastly different from the standard modeline reported in many xorg.conf fixes for the 226BW on these forums. The 226BW did come with three different panels, so perhaps this explains the difference. In any case, don't copy what I got above, make sure you generate your own.

3. Add this to xrandr (copy everything after Modeline) - for me this was:
```
$ xrandr --newmode "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
```4. Add an equivalent mode to xrandr using the external screen location you found in step 1 - for me this was:
```
$ xrandr --addmode VGA1 1680x1050_60.00
```5. Output this using the screen location and mode from step 4 - for me this was:
```
$ xrandr --output VGA1 --mode 1680x1050_60.00
```6. Fix your screen positioning using System > Preferences > Display - mine is always wrong every time I implement this fix.

To save having to do this every time, I turned the xrandr commands into a Bash script that I can run when using this screen:

```
#!/bin/bash

xrandr --newmode "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
xrandr --addmode VGA1 1680x1050_60.00
xrandr --output VGA1 --mode 1680x1050_60.00
```If you use this, remember to put in your modeline and screen location.

To make it executable just:

```
$ chmod u+x /path/to/your/script.sh
```Hypothetically, this approach should also work for other non-standard screens. However, given that my 226BW is still blurry in places after all this, your mileage with this approach (226BW or otherwise) may vary.

---

### Post by JuddGarratt on 2009-11-17
Incidentally, I can now confirm that the above approach also works with a ViewSonic VX2233WM - only this time with perfect results.

Very happy.

This leads me to suspect that the Samsung 226BW is just a non-standard problem monitor.

Aside: to move the Gnome panels to an external display, just right click them, hit Properties and then untick Expand. Panel then becomes draggable. Move to external display then retick Expand and you're good to go.

Took me ages to figure that out. Might save someone some Googling.

---

### Post by andremarra on 2010-10-27
WOW! After hours looking for some solution, this one really worked for me. And it is the simplest one!

I have a Toshiba A105-S4014 with an Intel 945GM graphics card and the Samsung 226BW plugged in (running Ubuntu 10.10 Maverick Meerkat). Thanks a lot!

---

### Post by latz-twn on 2010-10-27
Hi thx for this solution really helped me. I've upgraded to 10.10 and since then I had problem with an old screen of mine a Samsung SyncMaster 713N which was working great in Ubuntu 10.04 but since the upgrade it wasn't recognize correctly anymore and the resolution was not the right one. Anyways, this is a great for everyone using external screens that aren't recognized right away. 


Thanks a lot :)

---

### Post by JuddGarratt on 2010-10-29
No problem :)

You're right latz-twn, this trick works on pretty much any external screen. Since I stumbled upon the original solution, I've used this to fix resolution problems on everything from TVs to projectors.

Glad it helped

---

