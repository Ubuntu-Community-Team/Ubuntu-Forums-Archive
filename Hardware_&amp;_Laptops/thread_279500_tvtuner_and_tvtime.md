---
title: "tvtuner and tvtime"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by rufinojr54 on 2006-10-18
I have problem running Tvtime. I installed it using synaptic. I'm using Ubuntu 6.06. My video card is Flyvideo '98. It's in the device manager meaning detected and drivers are installed. In WindowsXP it is working properly. But when i tried to run Tvtime nothing happens. No window appears. Anyone knows what do I have to do? Please help. Thanks!

Rufino :confused:

---

### Post by faithsnathan on 2006-11-03
:confused:  I'm having a similar problem.  I installed tvtime with apt-get and can't get it to open.  I tryed opening the file by double-clicking on it, but nothing happened.  I tryed opening it by typing "tvtime" in the terminal, and got the following message:

> nathan@nathan-desktop:~$ sudo tvtime
Password:
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/nathan/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

nathan@nathan-desktop:~$


Any help would be appreciated.  Thanks!

---

### Post by faithsnathan on 2006-11-04
> **faithsnathan said:**
> :confused:  I'm having a similar problem.  I installed tvtime with apt-get and can't get it to open.  I tried opening the file by double-clicking on it, but nothing happened. 


Update:  I uninstalled tvtime and reinstalled it using Add/Remove.  Now, it opens up just fine.  However, I cannot figure out how to get my DVD player (which is hooked up to my TV card and, incidently, worked fine under XP) to work with this (or ANY) program.

rufinojr54:  I'm still a newbie to Linux as a whole and Ubuntu in specific, but I would recommend that you uninstall tvtime, run the update manager, and try adding the program again in the Add/Remove thing.  Good luck!

---

