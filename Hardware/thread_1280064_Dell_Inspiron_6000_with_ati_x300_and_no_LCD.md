---
title: "Dell Inspiron 6000 with ati x300 and no LCD"
date: 2009-10-01
forum: Hardware
---

### Post by seehymeh on 2009-10-01
I have a Dell Inspiron 6000 with an ATI Mobility x300, and I would like to install Jaunty.  When I used the Ubuntu desktop cd the installer failed with an error about Xorg not starting.  I retried using the graphics safe mode and it worked.  The problem is that the current xorg.conf shows the driver as vesa (cause the safe graphics) and I only have 1 option for resolution.

I think this is the root problem:
My LCD broke, so I removed it a couple years ago.  I have been using the laptop on a tv as a Media PC using an s-video cable.  This might be the cause.

I tried editing the xorg.conf but that didn't work.  I did a lot of stuff but I have a backup of the automatically configured vesa so that's not a big deal.  I changed the driver option to "ati" (or was it radeon? it was whatever the forum told me it was, I don't remember now) but I got a [EE] No drivers found.  I also tried to follow a howto for fglrx but that gave me a [ee] No devices found.  

Sorry I don't have more details right now (errors verbatim, config files, etc..,) but I won't be home for another 3 hours.

Basically, I'm not really sure where I should start looking, and I'd like to fix it tonight.  Is my lack of an LCD messing me up?  Is there something special I should put in the xorg.conf to make the s-video output the default?  What driver should I be using for this computer? Should I try a different distro for this machine? Any suggestions?

---

