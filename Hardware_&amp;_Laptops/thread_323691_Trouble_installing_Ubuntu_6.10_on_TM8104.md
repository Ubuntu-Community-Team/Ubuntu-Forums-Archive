---
title: "Trouble installing Ubuntu 6.10 on TM8104"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by Jim Link on 2006-12-22
Ok I followed the instructions by Ben Alex he gave here: [http://www.ubuntuforums.org/showpost.php?p=1224077&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1224077&postcount=4)
> 
I had the same problem on my Acer TravelMate 8104. The solution is:

1. Boot the live CD with the default options, and allow the screen to go blank.

2. CTRL ALT F1 to a different console.

3. sudo vim /etc/X11/xorg.conf
Find the Device section. Add a new line inside it:
Option "MonitorLayout" "LVDS, AUTO"

4. CTRL ALT F7 back to the X11 window.

5. CTRL ALT BACKSPACE to shutdown and restart. It will work.

Good luck

Ben


But when I get to step 2. I get a purple screen with a bunch of lines.  I can't read or do anything.  I tried to skip to step 4 just to see what would happen and the screen goes blank again.  Any help would be greatly appreciated...

---

### Post by Jim Link on 2006-12-22
Well I actually figured something out dealing with linux on my own...

what I did was used the command line installer and typed in:

live vga=771

this allowed me to see the gui installer perfectly.  Once it was installed I was able to complete the mods necassary to finish my install...  Thing works damn near perfectly now.

---

