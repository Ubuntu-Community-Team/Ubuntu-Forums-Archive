---
title: "setting up external display on thinkpad x301 - 10.04"
date: 2011-09-02
forum: Hardware
---

### Post by Fenriswolfr on 2011-09-02
I have an x301 with a display port and 30" monitor (no display port). I am using a displayport to dvi adapter and dual link dvi cable to connect it. 

The x301 has onboard intel graphics : Intel GMA 4500MHD

So the problem: the 30" monitor is stuck at 1200x800 resolution. It's the only option under system->preferences->monitors

Here is the results of xrandr:

> Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected (normal left inverted right x axis y axis)
   1440x900       60.0 +   59.9     50.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 646mm x 406mm
   1280x800       59.9* 
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)Trying to set with xrandr
xrandr --output HDMI1 --mode 2560x1600
results
xrandr: cannot find mode 2560x1600

Any suggestions?

Thanks

---

### Post by gordintoronto on 2011-09-02
I found this:
Flat panels up to 2048x1536 @ 60 Hz or digital CRT/HDTV at 1400x1050 @ 85 Hz

when I searched for "intel gma 4500mhd max resolution"

---

### Post by wartburgritter on 2013-04-02
Has someone found a solution ???

I own an ThinkPad X301 as well and I would like to buy an 30'' screen. I found following links and posted in an german forum.  The hardware works. BUT does it even using linux???

[http://www.thinkscopes.com/thinkpad-x301-supporting-wqxga-or-wqhd/](http://www.thinkscopes.com/thinkpad-x301-supporting-wqxga-or-wqhd/)

[http://www.thinkpads.com/forum/viewtopic.php?f=43&t=81492](http://www.thinkpads.com/forum/viewtopic.php?f=43&t=81492)

[http://forum.thinkpads.com/viewtopic.php?t=67691](http://forum.thinkpads.com/viewtopic.php?t=67691)

[http://thinkpad-forum.de/threads/157261-X301-maximale-Aufl%C3%B6sung-externer-Monitor](http://thinkpad-forum.de/threads/157261-X301-maximale-Aufl%C3%B6sung-externer-Monitor)

kind regards bernd alias der wartburgritter

---

### Post by wartburgritter on 2013-04-08
I just would like to confirm. I'm just writing from my x301. Attached at the display port using the cable which was with the monitor is a HP ZR30w running at a resulution 2560 x 1600. I'm running Debian wheezy. I did a xrandr --auto and changed at the kde systemsettings the resolution of the DP1 to 2560 x 1600. 

Wow its so huge

---

