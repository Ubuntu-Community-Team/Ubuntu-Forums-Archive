---
title: "Wrong external monitor detected, Help..."
date: 2008-09-27
forum: Hardware
---

### Post by ka7ple on 2008-09-27
Good Day, 

I am running Ubuntu on an older IBM T30 laptop. The OS runs great on it, however I am using an external monitor. Its a Planar 17". The resolution is 1280x1024. Ubuntu detected it as an 18" TVT monitor and I have the bottom and the right side of the desktop off the actual display area. I cant see the bottom tool bar or the power on/off icon on the top tool bar. 
Is there a way to force Ubuntu to change the external monitor from an 18" to a 17" LCD? I can't seem to find the command line tool I.E. Xconfig, or what ever Ubuntu uses. I tried changing the xorg.config but all that does is change the resolution. The OS still thinks its a 18" monitor. 
Can some one please help point me in the right direction.  
This was not a problem with any other Linux distribution. 

Thanks, 

Michael

---

### Post by overdrank on 2008-09-27
> **ka7ple said:**
> Good Day, 

I am running Ubuntu on an older IBM T30 laptop. The OS runs great on it, however I am using an external monitor. Its a Planar 17". The resolution is 1280x1024. Ubuntu detected it as an 18" TVT monitor and I have the bottom and the right side of the desktop off the actual display area. I cant see the bottom tool bar or the power on/off icon on the top tool bar. 
Is there a way to force Ubuntu to change the external monitor from an 18" to a 17" LCD? I can't seem to find the command line tool I.E. Xconfig, or what ever Ubuntu uses. I tried changing the xorg.config but all that does is change the resolution. The OS still thinks its a 18" monitor. 
Can some one please help point me in the right direction.  
This was not a problem with any other Linux distribution. 

Thanks, 

Michael

Hi and welcome, have you tried the command ```
gksu displayconfig-gtk
``` and change your screen there.

---

