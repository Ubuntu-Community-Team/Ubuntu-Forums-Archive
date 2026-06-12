---
title: "Fix for brltty interfering with USB devices."
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by eastburn on 2007-07-13
This is a non destructive way of disabling “brltty” that interferes with the use of some USB devices such as USB/serial Converters (aka adapters).  

This write up is for newbies (like myself) so if it seems overly detailed that is the reason.

A few typing short-cuts to define:
LMC = left mouse click
RMC = right mouse click
DLMC = double left mouse click
PCO = place cursor on

Do not include the <  > that encloses the word(s) to be typed in this write up.  OK, here we go.

1.From the desktop...LMC on Applications (very top left of desktop).
2.PCO Accessories.
3.LMC on Terminal.
4.Type <sudo -i>  press the <Enter> or <Return> key.
5.Type <nautilus> press the <Enter> or <Return> key.
6.From the tool bar.. LMC on the up arrow.
7.DLMC on the folder labeled  etc
8.DLMC on the folder labeled  udev
9.DLMC on the folder labeled  rules.d
10.DLMC on the file labeled  85-brltty.rules
11.Should see the gedit application appear with text displayed.
12.LMC on the gedit expand icon (very top right of gedit, middle icon,  looks like a square).
13.Starting from the very top row of text... add the <#> symbol followed by a space at the very beginning of every row not already starting with a <#>.
14.LMC on the gedit save icon (top left, looks like a floppy disk).
15.LMC on gedit close icon (very top right, the X on the right).
16.LMC on nautilus close icon (very top right, the X on the right).
17.Type <exit> in the Terminal window and press the <Enter or Return> key.
18.Again, type <exit> in the Terminal window and press the <Enter or Return> key.
19.Close all open application(s).
20.LMC on Systems (very top left of desktop) and LMC on Quit.
21.LMC on restart.

Once the computer restarts and the desktop is displayed, you should be able to use your USB device.
Let me know if this works for you (did for me) or if something in the instructions is unclear.

---

### Post by newpants2003 on 2007-07-25
just tried your way, but the "ttyUSB0 file flash on the screen then disappear" problem isnt sovled......

start missing winXP now

---

### Post by benizra on 2008-02-12
I am also having the same problem.  The pl2303 USB to serial I am using keeps flopping from ttyUSB0 to ttyUSB1.

I am experiencing this on Ubuntu only. I have Fedora Core 4 and CentOS 4.4 with the same device but there is no problem.

HELP!!!

---

