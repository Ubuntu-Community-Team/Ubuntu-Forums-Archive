---
title: "touchpad: synclient not reflecting changes made to xorg.conf"
date: 2005-11-13
forum: General Help
---

### Post by beijingjj on 2005-11-13
Just moved to Ubuntu from Mepis (after a miserably failed attempt at suse 10.1).  Everything is mostly working right out of the box, quite nice, except that I need to tweak my touchpad settings.

I edited my /etc/X11/xorg.conf to add the line

  Option          "SHMConfig"             "on"
 
to my Synaptics section.  I then used the command "synclient -l" to determine the current settings and make changes to the xorg.conf, for example I changed my "MinSpeed" and "MaxSpeed."  However when I restart X or even reboot the computer synclient still holds the same original values, it doesn't seem to be reading the values that I put into xorg.conf.

Anyone know what's going on?

Thanks.

---

### Post by quixote on 2006-11-04
I have the exact same problem ... a year later and using Edgy.  Hmm.

Help?

---

