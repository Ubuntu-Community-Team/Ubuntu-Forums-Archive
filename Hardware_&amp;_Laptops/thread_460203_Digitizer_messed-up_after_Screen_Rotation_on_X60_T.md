---
title: "Digitizer messed-up after Screen Rotation on X60 Tablet"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by Tilo on 2007-05-31
after going in to Preferences->Screen-Resolution, and selecting anything other than 'normal',
the screen rotates (that's good) - but the digitizer coordinates get mapped wrong.

E..g if I select "inverted" and then move the mousepointer left, it goes right.. that's wrong!
Another way to test this on a tablet is to just point the pen at a screen-point, but the mouse-
pointer goes somewhere else, not under the tip of the pen.. :p

I guess this should be submitted as a bug.  Or is this a known issue which has a fix? 

Please advise how to post bugs

---

### Post by freund on 2007-06-04
I had a similar issue and had to write a script that corrects this. For standard resolution 1024x768 the script is ( for invert):

#!/bin/bash
    xrandr -o inverted
#3 - means upside down
    xsetwacom set stylus Rotate 3
    xsetwacom set eraser Rotate 3
    xsetwacom set cursor Rotate 3

    xsetwacom set stylus BottomX 24600
    xsetwacom set eraser BottomX 24600
    xsetwacom set cursor BottomX 24600

    xsetwacom set stylus BottomY 18500
    xsetwacom set eraser BottomY 18500
    xsetwacom set cursor BottomY 18500

Now for 90deg rotation its:
!/bin/bash
    xrandr -o left

    xsetwacom set stylus Rotate ccw
    xsetwacom set eraser Rotate ccw
    xsetwacom set cursor Rotate ccw

    xsetwacom set stylus BottomX 18500
    xsetwacom set eraser BottomX 18500
    xsetwacom set cursor BottomX 18500

    xsetwacom set stylus BottomY 24600
    xsetwacom set eraser BottomY 24600
    xsetwacom set cursor BottomY 24600

 and finally for clockwise rotation:


#!/bin/bash
    xrandr -o right

    xsetwacom set stylus Rotate cw
    xsetwacom set eraser Rotate cw
    xsetwacom set cursor Rotate cw

    xsetwacom set stylus BottomX 18500
    xsetwacom set eraser BottomX 18500
    xsetwacom set cursor BottomX 18500

    xsetwacom set stylus BottomY 24600
    xsetwacom set eraser BottomY 24600
    xsetwacom set cursor BottomY 24600

hope this is helpful.

regards
al

---

### Post by Tilo on 2007-06-14
cool - i'll try that.. 
thank you!

---

### Post by osarusan on 2007-07-07
Hi, that script looks great. I need the same thing. Can you tell me how to install and run this script? Is there a way to make it run automatically upon rotate, or would I have to right click and run it each time I rotate? I'm really new to this so any explanation would be great. Thanks! :-)

---

### Post by freund on 2007-07-12
I found a better script at the following web site. I have switched to that and it has a step by step procedure.

The best place for configuring the X60 is at [http://www.thinkwiki.org/wiki/Instal...d_X60_Tab](http://www.thinkwiki.org/wiki/Instal...d_X60_Tab) let
which points to
[http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)
but will soon be transfered to the first site.

It has everything about configuring buttons/screen rotation/pens ...etc

with some ubuntu specific stuff by searching x60 tablet here at this forum
good luck
al

---

