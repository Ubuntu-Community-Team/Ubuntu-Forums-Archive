---
title: "Resolution on old laptop"
date: 2011-01-31
forum: Hardware
---

### Post by cpeachey on 2011-01-31
I have a Toshiba Satellite 4080XCDT laptop with Ubuntu 4.10 running ok. RAM is 192mb.
The maximum screen resolution offered is 600x800 so I have a large area around the edge of the window that is blank. How can I get the 1024x768 resolution that will fill the whole screen?
The video chip seems to be a "Trident Cyber 9525 DVD"
I have looked at /etc/x11/org.conf but this file is empty.
Chris

---

### Post by overdrank on 2011-01-31
> **cpeachey said:**
> I have a Toshiba Satellite 4080XCDT laptop with Ubuntu 4.10 running ok. RAM is 192mb.
The maximum screen resolution offered is 600x800 so I have a large area around the edge of the window that is blank. How can I get the 1024x768 resolution that will fill the whole screen?
The video chip seems to be a "Trident Cyber 9525 DVD"
I have looked at /etc/x11/org.conf but this file is empty.
Chris

Hi and 4.10 is quite old. :) But try /etc/X11/xorg.conf

---

### Post by cpeachey on 2011-01-31
X11 folder contains a file called XF86Config-4 which HAS references to 1024x768 as well as 800x600 and 640x480 but I cannot see anywhere that would add the 1024x786 resolution to the options in sys config/screen resolution so..........
I think I will look for a different distro. Ubuntu is my favourite but will later versions not install due to lack of ram. (I have 10.10 on the desktop pc) I only want the laptop for showing photos. Editing (and finding!) the right files is a bit beyond me.
Chris

---

### Post by Claus7 on 2011-01-31
Hello,

not an answer to your problem, yet in a similar situation I added xubuntu on a box (either lucid or maverick-not remember exactly) and it worked like a charm. You might conciser this option...

Concerning your issue, and with that chip, you might have to do a lot of tweaking with xorg.conf in order to make it work, yet you might not. I would try to create a new one and try to add lines about resolution. 

Regards!

---

### Post by Kirboosy on 2011-01-31
If I may throw a suggestion out there...You could try updating to a newer version of Ubuntu. [lUbuntu]("http://lubuntu.net/") or [Xubuntu]("http://www.xubuntu.org/")

It might have some driver that will fix your issues. 4.10 is really really old... If that doesn't fix it then we can troubleshoot farther more easily.

---

