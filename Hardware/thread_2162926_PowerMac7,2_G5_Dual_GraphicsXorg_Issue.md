---
title: "PowerMac7,2 G5 Dual Graphics/Xorg Issue"
date: 2013-07-16
forum: Hardware
---

### Post by webmonkey44 on 2013-07-16
I installed Kubuntu alternate 12.04 LTS on my power7,2 with 4gig of ram, 1 terabyte hard drive(guided entire disc partitioning),nvidia (9xxx i think) serious graphics(im not sure which variant at this moment if you have an easy software test tell me).
When i did the Xorg doesnt work properly the gdk/kdm login screen will load(the bottom half of half one color wall paper is black for a second) then i login to kde and the loading screen works fine til the last thing comes up then the screen changes first the top or bottom flashed black then the screen goes black and x stops dead though the mouse moves fine. you cant even load X using apps from command line.

I tried to uninstall mesa/glx whatever, but system said it wasnt there and i couldnt check for sure with synaptic. I then tried a safe generic Xorg.conf in the /etc/X11 folder plus setting boot to include "nomodeset". no difference either. 
I tried "dpkg-reconfigure xserver-xorg" and "dpkg-reconfigure -phigh xserver-xorg" and this did not bring up a manual configuration interface.
I remember a previous live version of ubuntu working fine on this machine when it came to X11.

Can someone provide a method which works with the 12.04(it has the latest updates as all the rest of the sytems are fine)?

---

