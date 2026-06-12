---
title: "Monitor Not Detected"
date: 2009-10-12
forum: Hardware
---

### Post by nalcomis on 2009-10-12
I recently installed Ubuntu 9.10B on a relatively older model Dell workstation with an attached Dell monitor.  Ubuntu isn't correctly detecting my monitor and will only allow me to do resolutions up to 800x600.  I have seen several posts specifying configuration items within the /etc/X11/xorg.conf file, but this file does not exist on my machine.  
 
Can somebody point me in the right direction in regards to specifying additional resolutions and what file I need to edit to tweak X?
 
I apologize if this has been addressed before, but I couldn't find anything within the forum regarding this problem specifically.
 
Thanks in advance...

---

### Post by Mark Phelps on 2009-10-13
Suspect your limitation is not the monitor but the video card/chip resident in the PC.  To find out what you have, open a terminal and type "lspci".  That will list all the devices connected to the PCI bus, one of which will be the video card/chip.  Post back what you find out.

---

