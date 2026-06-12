---
title: "lost windows file sharing and printer"
date: 2008-07-26
forum: General Help
---

### Post by drdmac1 on 2008-07-26
I feel I have been too stupid for words and would appreciate some help. I have a small home network - two Ubuntu 8.04 machines and one Windows XP.

While fiddling with file sharing a dialog box appeared, something to do with windows sharing but I did not read it closely, and answered yes to continuing. Immediately after I found I could no longer access my Windows machine from either of my Ubuntu machines. I also have an HP Officejet Pro networkable printer which is no longer available from either of my Ubuntu machines but still prints from my XP machine.

I don't know whether I have installed something I did not understand or removed something I should not have.

The user log shows this when I try to print.

Jul 26 10:24:58 david-desktop Officejet_Pro_L7500?ip=192.168.1.4: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Jul 26 10:25:02 david-desktop Officejet_Pro_L7500?ip=192.168.1.4: io/hpmud/jd.c 84: unable to read device-id 
Jul 26 10:25:02 david-desktop Officejet_Pro_L7500?ip=192.168.1.4: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Jul 26 10:25:02 david-desktop Officejet_Pro_L7500?ip=192.168.1.4: prnt/backend/hp.c 636: INFO: open device failed; will retry in 30 seconds... 

Sorry about the vagueness - and stupidity. Any help appreciated

A few days later - I appear to have enabled "windows shares". When I access the "windows network" a few folders appear but I can no longer directly access the hard drive. The changes have also affected my second linux box although I was not working on that.

Still vague I am afraid. How can I switch off or uninstall "windows shares"

---

### Post by AaronLS on 2008-07-26
Are you able to ping the windows machine from the linux machine?

ping computerNameHere

---

### Post by drdmac1 on 2008-07-26
It doesn't look like it.

ping: unknown host drmac

---

