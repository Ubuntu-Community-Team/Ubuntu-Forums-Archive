---
title: "PCMCIA Card Slots not working in 8.04"
date: 2008-09-03
forum: Hardware
---

### Post by unverviking on 2008-09-03
I have an IBM T-23 Laptop Type 2647, and with 8.04 loaded, and my PCMCIA card slots are not working.  I have a Cisco Aironet 350 PCMCIA wireless card, it works fine in 7.10.  I have checked status of both ports, and it seems to always think that something is in it, but nothing works in either slot.  I ended up taking another HD and installed 8.04, and test it periodically, I am using it now, with a wired connection.  I was hoping that eventually there would be a patch, or a fix that would take care of it, but even after loading 184 updates today, still nothing...  Any help, suggestions ??

---

### Post by albrt741 on 2008-10-28
Hi, quite same problem with my IBM T30. Had 7.10 and worked fine; upgraded to hardy and pcmcia detection is not working now.
Tried pcmcia-to-usb card and token-ring card and umts-modem; no go. 
pccarctl gives no output
nothing from dmesg and /var/log/messages either. 

Alberto

---

