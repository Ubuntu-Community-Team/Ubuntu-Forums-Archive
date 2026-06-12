---
title: "Trackpad scroll area too wide"
date: 2010-04-12
forum: Hardware
---

### Post by dilodicus on 2010-04-12
I've been using Ubuntu on my Gateway ML3108b laptop for about 2 months now, I had a few teething issues with Karmic but since upgrading to Lucid pretty much everything works fantastically, I am smitten and don't see why I'd ever want to go back to using Windows on this machine.

However there is one small problem I've had since day one which I can't seem to find a solution for anywhere, the area of my synaptics trackpad that is used for vertical scrolling is too wide... there is a physical ridge on the surface of the pad that separates the main pad from the vertical scroll section, but in Ubuntu for some reason it has assigned some of the main trackpad for scrolling as well. This means I often accidentally scroll when just trying to move the mouse pointer. 
I have tried playing with the options in the touchpad settings but nothing there seems to help.
I didn't used to have this problem with Windows so it must be a software issue, and I was wondering if anyone might know if there is a way to tell Ubuntu to change the width of the scrolling area, even if it means a lot of trial and error to get it just right.

Any help on this issue would be really appreciated
thank you :)

---

### Post by xixs on 2010-06-21
I have the same laptop, try typing the following into a shell

synclient RightEdge=7000

Unfortunately it forgets that setting on a reboot and I'm not sure where best to save it so I just run that command on startup.

---

### Post by dilodicus on 2010-06-23
Thankyou so much for the reply, 
unfortunately about a week ago my trusty gateway finally bit the dust, tried replacing cpu and ram but got no response from it. :(
 
hopefully that will still be useful for others on the forum! Thank you again!

---

### Post by leftkidney on 2011-03-05
I have the same problem, except I cant edit the xorg.conf file

in 10.10 its in the /usr/share/X11/xorg.conf.d location for some reason

I think I need to edit the 50-synaptics.conf file but I tried gedit with sudo even su first but I cant edit it

what am I doing wrong?

---

