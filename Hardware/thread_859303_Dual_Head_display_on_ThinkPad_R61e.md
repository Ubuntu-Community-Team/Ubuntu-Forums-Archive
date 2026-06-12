---
title: "Dual Head display on ThinkPad R61e"
date: 2008-07-14
forum: Hardware
---

### Post by short4lif2 on 2008-07-14
Does anyone know how to establish a dual montor setup on a thinkpad r61e?  I understand that intel does not make drivers for the intel 965 card, but is a dual head setup possible using the XORG driver?  My initial attempts were usng Xinerama.  Perhaps there are other methods of achieving a dual head setup?  Any suggestions would be appreciated.

---

### Post by prshah on 2008-07-14
> **short4lif2 said:**
>  I understand that intel does not make drivers for the intel 965 card

Ooohhh... Intel does in fact have a driver available for 965 cards; give the command ```
sudo displayconfig-gtk
```, then switch to the "graphics card" tab, and select the "Intel Experimental Modesetting" driver, or just plain "intel". Don't select "i810". If you do not have the "intel" driver, give the command ```
sudo apt-get install xserver-xorg-video-intel
``` to get it.

You can then setup a dual head config using System-Preferences-Screen Resolution; connect your external display, then use the "Detect Displays" button. However, in some cases, I have heard that dynamic configuration does not work in Hardy's Xorg; in this case, both displays have to be connected before X is started up.

From Hardy onwards, the focus is to remove dependence on the Xorg.conf file... while currently it does not ignore settings in the Xorg, it may do away with the file altogether in future versions...

---

### Post by short4lif2 on 2008-07-14
prsha- Thank you so much!! I finally have so much working that I did not before!  You were a great help.  I've made great progress with the second monitor in that it is cloning my primary display, but somehow when i uncheck the clone feature and click apply, it remains mysteriously stuck at the cloning stage.  I am going over my xorg.conf trying to figure out where the missing link is.  Once again thanks for that!

---

### Post by short4lif2 on 2008-07-15
Anyone?

---

### Post by short4lif2 on 2008-07-16
Bump

---

### Post by prshah on 2008-07-17
> **short4lif2 said:**
> 
made progress with the second monitor in that it is cloning my primary display, but somehow when i uncheck the clone feature and click apply, it remains mysteriously stuck at the cloning stage. 

I'm not sure but I don't think that dynamic display capabilites are quite ready in Xorg yet. I think you will have to have the secondary display connected when starting up X (essentially during bootup), then uncheck "Clone displays" (click apply) then logout and restart X (Ctrl+Alt+BkSpace). 

This information is totally untested, and might be termed a vague guess.

---

### Post by short4lif2 on 2008-07-18
Well, thanks for your help with the drivers.  If I manage to dig up a solution to the dual head problem, i'll post back.  Thanks again for trying.

---

