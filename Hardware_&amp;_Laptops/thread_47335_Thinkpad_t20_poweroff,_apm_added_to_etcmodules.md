---
title: "Thinkpad t20 poweroff, apm added to /etc/modules?"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by Nasso on 2005-07-08
I got some poweroff problem with my ibm thinkpad t20 running Ubuntu. 

Found this in the wiki ( [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM) )

> 
Needs 'apm' added to /etc/modules in order for it to shut off correctly at power down, and to also let the battery applet display anything. Needs 'Option "HWCursor" "false"' adding to /etc/X11/XF86Config-4 for black cross not to appear after boot up. 


WTF does this mean? ^_^ im kind of a n00b.

thanks...

---

### Post by varunus on 2005-07-08
Well, the first statement means that you need to load the "apm" kernel module.  The instructions on how to do it are there; open up your /etc/modules file using "sudo gedit" from a console, and add the line apm at the end of it.

The Option "HWCursor" "false" needs to be added to /etc/X11/xorg.conf.  Open it up with sudo gedit, and scroll down to the device section.  Your video card should be listed there; add the line
```

Option "HWCursor" "false"
```

right before the "End Section".

Good luck.

---

### Post by Nasso on 2005-07-09
[QUOTE=varunus]Well, the first statement means that you need to load the "apm" kernel module.  The instructions on how to do it are there; open up your /etc/modules file using "sudo gedit" from a console, and add the line apm at the end of it.

The Option "HWCursor" "false" needs to be added to /etc/X11/xorg.conf.  Open it up with sudo gedit, and scroll down to the device section.  Your video card should be listed there; add the line
```

Option "HWCursor" "false"
```

right before the "End Section".

Good luck.[/QUOTE]
 great :) thanks!

---

