---
title: "wide-screen resultions on Intel graphics controller?"
date: 2008-09-09
forum: Hardware
---

### Post by gradedcheese on 2008-09-09
Hi.  I have a desktop PC with the Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02), which I think is a GMA 900 series adapter.  The regular resolutions seem to work fine but I cannot get it to display 1680x1050 which I need for my new monitor.  I booted the PC into Windows XP and found that it displayed the correct resolution, so the hardware is certainly capable.  Any suggestions for how to configure X on Hardy?  Should I build a newer driver?  Thanks!

---

### Post by veloce on 2008-09-10
I suggest you try xrandr.  I haven't had to use it with Hardy but did a fair bit with it and Gutsy.  It detects most things going on with the monitors and can change most settings.

---

### Post by gradedcheese on 2008-09-11
Yeah, I tried that.  It detected several available resolutions but not any wide-screen ones.  For now, I've installed a Radeon 7000 PCI card which does the job (at the right resolution) as a workaround, but it would be nice to have the onboard video work since I now know that it can do 1680x1050 in theory.

---

### Post by veloce on 2008-09-11
I see there is a new version of the intel driver in my updates this morning - does it help any?

---

