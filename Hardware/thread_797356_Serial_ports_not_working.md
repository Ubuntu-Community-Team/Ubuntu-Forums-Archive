---
title: "Serial ports not working"
date: 2008-05-17
forum: Hardware
---

### Post by gewitty on 2008-05-17
Can anyone tell me how I can check if my serial ports are active and working, and if not, how I can enable them (I'm running Ubuntu 8.04)?

I am using the Viking GPS Manager application, but it seems unable to connect with my Garmin device, which I've tried on both ttyS0 and ttyS1 ports. Every time I try to upload or download info to or from the Garmin, I get an error saying that the GPS device is not available.

Any help would be appreciated.

P.S. Just found a brief note on another forum, saying that there is a bug in 8.04 which can prevent serial ports from operating. Can anyone confirm if this is true and if any workaround exists?

---

### Post by bmilne on 2008-05-19
Have you tried running the software as sudo?  It may be your user priviledges cannot access the serial port.  You could try running a serial comms program, like minicom or gtkterm, to see if they can access your serial ports. 

cheers

---

