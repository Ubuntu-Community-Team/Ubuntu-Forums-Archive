---
title: "Screen Resolution for Dell Inspiron Mini"
date: 2011-05-15
forum: Hardware
---

### Post by phillip4672 on 2011-05-15
Hi - I previously posted this in the "Video & Multimedia" Forum, but think it may be better off here. The smiley faces aren't intentional. They just appeared after I pasted the original output from the commands I used. I suppose I need to escape them somehow...
----------------------------------------------------------------------------------------------------------
Hi,
 
Please help!
 
I am stuck in 800x576 resolution and don't know how to escape. I've tried changing xorg.conf but that caused my machine to grind to a halt and I had to copy the original .conf file back over before I could launch GNOME again. I've run lspci | grep VGA, and this is what I get:
 
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
 
When I run xrandr --verbose, I get:
 
Screen 0: minimum 800 x 576, current 800 x 576, maximum 800 x 576
default connected 800x576+0+0 (0x10:cool: normal (normal) 0mm x 0mm
Identifier: 0x107
Timestamp: 30685
Subpixel: horizontal rgb
Clones: 
CRTC: 0
CRTCs: 0
Transform: 1.000000 0.000000 0.000000
0.000000 1.000000 0.000000
0.000000 0.000000 1.000000
filter: 
800x576 (0x10:cool: 0.0MHz *current
h: width 800 start 0 end 0 total 800 skew 0 clock 0.0KHz
v: height 576 start 0 end 0 total 576 clock 0.0Hz
 
The display GUI is useless!
 
Does anyone know how I can progress?
 
I'm trying to install Photran for Eclipse 3.6. I've managed to get 3.6 and it works but the next step involves choosing a package that I just can't see because my screen resolution is too small.
 
Kind regards,
 
Phillip

---

### Post by phillip4672 on 2011-05-29
Hi, 

I am still having trouble with this despite my best efforts.

I am working my way through the Ubuntu Wiki ([https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions)) on the subject and have tried the following:

-running cvt with parameters 1024 and 768, i.e

$cvt 1024 768

which gives the following output:

# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

-running xrandr --newmode with the information from cvt. Like this:

$xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

-running xandr --addmode default 1024x768_60.00

(running xandr --addmode default 1024x768 returned the following error: xrandr: cannot find mode "1024x768")

-finally running xrandr --output default --mode 1024x768_60.00

but this also returned an error:

xrandr: Configure crtc 0 failed.

If anyone knows what's going on here I would be very grateful to know about it!

Kind regards,

Phillip

---

### Post by phillip4672 on 2011-05-31
Hi,
 
I think I'm getting to the bottom of this...
 
After going on IRC #ubuntu, I found someone who identified my chipset as GMA500. There is a long history of people trying to get to grips with it.
 
A user called Lucazade has come up with a solution and the details are on this forum, here:
 
[http://ubuntuforums.org/showpost.php?p=9587446&postcount=1406](http://ubuntuforums.org/showpost.php?p=9587446&postcount=1406)
 
There are also some notes with the repository, which is here:
 
[http://code.google.com/p/gma500/wiki/PPARepository](http://code.google.com/p/gma500/wiki/PPARepository)
 
I'm going to try this out later today.
 
Kind regards and with thanks to Lucazade,
 
Phillip

---

