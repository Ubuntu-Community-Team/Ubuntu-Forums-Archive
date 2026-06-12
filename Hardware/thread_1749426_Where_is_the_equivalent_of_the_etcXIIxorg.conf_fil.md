---
title: "Where is the equivalent of the /etc/XII/xorg.conf file?"
date: 2011-05-04
forum: Hardware
---

### Post by Jamface on 2011-05-04
I am trying to run Xubuntu from liveCD on my aging Sony PCG-FX109K laptop (Pentium III, 256 RAM, 80 GB HDD, 1400x1050 screen).  But Xubuntu cannot set up the screen resolution properly nor the refresh rate. All I get at boot is s flickering screen with 800x600 resolution.  The screen utility in the Xfce Settings Manager does not include a 1400x1050 resolution option.  I thought I might try editing the xorg.conf file but can't find it.  I guess more recent versions of Ubuntu have changed a bit, so the Monitor and Screen specifications are in another file.  Can someone tell me where, please. 
Many thanks
Bill

---

### Post by Yellow Pasque on 2011-05-04
Modern Ubuntu installs don't have an /etc/X11/xorg.conf by default, but you can create it.

---

### Post by Jamface on 2011-05-04
If Ubuntu no longer has this file where does it store its monitor and screen settings?  I could create a /etc/XII/xorg.conf file but I don't know what to put in it or how to make the computer use it! My 10.04 Ubuntu on my desktop does have such a file but it is quite different from the xorg.conf file Puppy Linux uses on the laptop I am trying to get to run Xubuntu. I was hoping I could edit the xorg.conf file in Xubuntu to include the monitor and screen settings in the Puppy xorg.conf file.  But it looks as if this might not work even if I could find where Xubuntu keeps the monitor and screen settings. Is this the case?

Another option occurs to em.  How can I make Xubuntu include 1400x1040 resolution as an option in the Xfce 4 Settings Manager Display utility - in such a way that 1400x1040 resolution will be used?

---

