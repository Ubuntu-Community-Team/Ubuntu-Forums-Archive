---
title: "Monitor Resolution Capability Not Fully Utilized"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Bobryuu on 2007-03-11
I'm very green at any Linux in general.  I've a new monitor for my computer, but it won't recognized that the monitor's resolution can be set at 1280X1024 if not 1600x1200.  The highest it will go is 1024x768.

What should I do?  What information do I need or do you need to help me and where do I find it?

Thank you

---

### Post by Cyphon on 2007-03-11
I'm having the same problem.  I have an Nvidia 7800 and I can't get the resolution up to 1600x1200.  Currently the highest I can get is 1280x1024.

---

### Post by steve0921 on 2007-03-11
The first thing to try is making sure X is set up so that it can use higher resolutions. There are two (roughly equivalent) ways to do this:


Before either method run ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` to make a backup copy of your current configuration (because breaking it is very bad). To restore your current imperfect configuration, run cp again with the arguments reversed.


**Method 1.** If you've never changed your xorg.conf yourself, run ```
sudo dpkg-reconfigure xserver-xorg
``` this will ask you a lot of questions about your setup of input devices and graphics. At one point, you will be able to indicate which resolutions you'd like available. If there are any options you don't understand, it is mostly safe just to use a default value.

[B]
Method 2.[/B] If you don't want to reconfigure all of xorg, you can manually change the configuration file in the necessary parts (instead of letting dpkg-reconfigure do the work). To do this run ```
gksudo gedit /etc/X11/xorg.conf
``` and find the > Section "Screen" portion. Then, for each "Display" subsection, add new resolutions before the existing ones on the Mode line so it looks like > Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

After reconfiguration you (hopefully) just need to restart X. The easiest way to do this is to save all of your work and press Ctrl+Alt+Backspace.

Best of luck!

---

### Post by Bobryuu on 2007-03-11
Thank you, that worked beautifully.

---

