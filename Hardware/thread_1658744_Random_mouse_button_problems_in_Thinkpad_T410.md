---
title: "Random mouse button problems in Thinkpad T410"
date: 2011-01-03
forum: Hardware
---

### Post by grappler on 2011-01-03
My problem is that in a random but frequent fashion left click on the laptop mouse buttons fails to work and that, again frequently, random pastes from the clipboard appear in the window where the cursor is placed. I can usually get left click to work again by switching to another workspace and back with the keyboard, or by first right clicking in the appropriate space on the desktop - or often by just waiting for several seconds. When the random pastes start, in say a terminal window, more pastes can be triggered by just rocking the computer back and forth. They do not happen when I am not touching the machine. 

The occurrence of these two problems  is not consistent and I can discern no pattern that specifically triggers them. When they do  occur the machine becomes essentially unusable.  I have searched the web and the ubuntu forums for others reporting this behaviour, and can find nothing closely related.   

All of this leads me to wonder whether  I have is a hardware fault or a software bug. The machine is  a Lenovo Thinkpad T410 with an SSD drive and discrete (NVidia) graphics. I am running Maverick 64 bit with the nvidia-current driver. Turning compiz on or off has no effect on the behaviour. I have recently done a clean install of everything to try to fix the problem - to no avail.  

To try to stop this behaviour I have also disabled the touchpad in the bios - which by the way has just been upgraded to the latest version - but this does not affect the problem either.

---

### Post by beenny on 2011-01-03
I think I have a similar problem with my Dell Latitude D630 running 10.04.

My touchpad works fine. However when I use my Logitech wireless mouse I get a lot of the same problems. I thought it may be a graphics problem and tried disabling compiz but that didn't solve anything. Now I can't get compiz working again. I get this error:

[Mon Jan 03 ~]$compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!


Any thoughts would be really appreciated...

bg

---

### Post by phil_bell on 2011-01-15
Hi grappler, it seems like I have some of the same issuses as you, but not everything. I posted a reply in similar thread and rather than repeat it here I'll include a link to my post in that thread.
[URL="http://ubuntuforums.org/showthread.php?p=10360393&highlight=left+click+pastes+clipboard#post10360393"]
http://ubuntuforums.org/showthread.php?p=10360393&highlight=left+click+pastes+clipboard#post10360393[/URL]

---

### Post by grappler on 2011-01-18
Just to wrap this up - it was a hardware fault which Lenovo fixed by replacing the keyboard.  The laptop is under a year old btw and the Lenovo engineer who fixed it claimed that the problem was due to "extensive use of the trackpoint"!

---

### Post by rbeswick on 2012-03-06
Out of warranty Lenovo T61. After searching everywhere for a solution I removed the plastic bezel containing touchpad and unplugged it and now I use a bluetooth mouse. As soon as I disconnected the touchpad all my troubles went away.

---

