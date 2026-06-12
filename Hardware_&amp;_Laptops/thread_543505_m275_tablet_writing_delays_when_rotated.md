---
title: "m275 tablet: writing delays when rotated"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by summersab on 2007-09-05
Odd problem. I got wacom-tools and wrote the scripts necessary to make my Gateway M275 rotate appropriately. However, when rotated (and ONLY when rotated), my writing in Xournal has delays. For instance, if I try to draw a line, the line only partially shows up when I am drawing and then fully appears maybe 100ms after I pick up the stylus. If I try to draw another line before that 100ms, the line never fills in and stays as a choppy line. This becomes a huge problem when I am writing at normal speed. Instead of having darkened text, I get a lot of really choppy and dotted sketch marks where text SHOULD be. When not rotated, this is not a problem. It just really stinks when trying to take pages of notes quickly - too much scrolling, etc.

Secondary note - what are the keymappings for for the buttons on the LCD panel? I tried finding them through the prompt (using the xar or xdr program or whatever), but it didn't return anything. Is there a way to make them work? That and the other hot keys are linked to F1 and others (hitting the mail button pops up help). Any ideas?

---

### Post by frith on 2007-09-05
Hmm... not sure if this has anything to do with your problem, but I do know that the hardware acceleration doesn't work in all orientations - eg on my Toshiba m200 any 'secondary' orientation is software rendering only. I think that I only get hardware acceleration in primary landscape mode.

But like I said, this may not be the issue.

---

### Post by smittex on 2007-09-06
i have been having some issues with ubuntu + m275 as well.  I have successfully got the screen to rotate with xrandr + (xrandr panel applet), though when it is rotated, the x & y coordinates for the stylus and mouse seem to be flipped.  (still looking for a solution for this).  i have used Gournal both in landscape and left orientation without any delays.  btw, im using feisty.

do you mind posting your script so i can use it and possibly see if i can recreate the issue?  

secondly, i havent tried it yet, but there is some tool for mapping out multimedia buttons on keyboards that i think will help find the lcd mappings.  again, i havent gotten around to this, so i dont know if itll work.

---

### Post by andrewsben on 2007-09-21
smittex - Are you just using xrandr or xrandr and setting the wacom orientation as well?  I have been using a command like this, in term, and it seems to work...

xrandr -o 3 && /usr/bin/xsetwacom set stylus rotate 1

Also I need to find out how to use the lcd buttons, any luck from anyone in this discussion.

ben

---

### Post by andrewsben on 2007-09-21
Here is a python script that I wrote just now to handle rotation of the screen.  I have spent the last couple of hours trying to get the keycode for the hardware keys but have been unsuccessful.  So I just wrote this and created a launcher for the panel, it will work fine until I can find out how to bind the hardware keys (if i can).

-------------------------------------------------------

#!/usr/bin/python
import os

stdout_handle = os.popen("xrandr | grep Current | grep rotation", "r")
current_orientation = stdout_handle.read().replace("\n","").replace("Current rotation - ","")

if (current_orientation == "normal"):
     os.system("xrandr -o 1 && xsetwacom set stylus rotate 2")
elif (current_orientation == "left"):
     os.system("xrandr -o 2 && xsetwacom set stylus rotate 3")
elif (current_orientation == "right"):
     os.system("xrandr -o 0 && xsetwacom set stylus rotate 0")
elif (current_orientation == "inverted"):
     os.system("xrandr -o 3 && xsetwacom set stylus rotate 1")

--------------------------------------------------------

EDIT:

it looks like the tabs are not showing up in the html rendering I just tried &nbsp's.  If this doesn't work, make sure that the os.system commands within the if statements are tabbed.

RE-EDIT:

Cannot get the &nbsp to work, just make sure that os.system commands are tabbed.  And for some reason a space is showing up in "Current rotation - ", make sure it has no space in Current.

---

