---
title: "no signal in dual monitors after logging in"
date: 2015-06-06
forum: Hardware
---

### Post by brad18 on 2015-06-06
I am running Kubuntu 14.04 with a Nvidia GeForce GT 610 and dual  monitors both DVI.  I've been running this rig for almost a year with no  problems until recently.  
I am having trouble running both monitors now. 
Both monitors have a signal and work at the kubuntu login (lightdm?) but  as soon as I login into KDE  they no longer receive any signal.  
If i run either monitor one at a time it works fine but both loose all  signal after logging in.  Funny when they both work before logging in.

Switching to a vterm i see: /usr/bin/X running and lightdm running
After logging in and have no signal, a ctrl-alt-backspace to kill X will  bring up the login manager again and both monitors work  again.

All help would be appreciated.  Here is what I've tried so far:
I've tried reinstalling the nvidia drivers: > sudo apt-get purge  nvidia*; sudo apt-get install nvidia-current; sudo apt-get install  nvidia-settings; sudo dpkg-reconfigure nvidia-current; sudo  nvidia-xconfig; sudo reboot.
I've tried both the nvidia-xconfig xorg.conf and no xorg.conf.

---

