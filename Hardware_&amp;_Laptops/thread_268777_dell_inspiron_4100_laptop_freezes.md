---
title: "dell inspiron 4100 laptop freezes"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by sarahsiggy on 2006-09-30
I'm a newcomer to Ubuntu and Linux, and I've read some of the posts about laptops freezing, but I'm not sure how to go about implementing the posted solutions on my machine.  My inspiron 4100 randomly freezes . . . any referrals or instructions would be greatly appreciated :)

---

### Post by kondor on 2006-09-30
You can check the system log - System<Administraiton<System Log after it freezes and upon reboot and save the log. Then you can post it for help. You need to isolate the precipitating event or last event prior to the freeze if you can. It is also helpful to include within the post the hardware details such as processor model, RAM installed, video card model, etc.

Good luck.

---

### Post by sarahsiggy on 2006-10-02
Here are the logs for right before and after it froze:

Oct  2 17:19:16 sarah-laptop hpiod: 0.9.7 accepting connections at 56135... 
Oct  2 17:19:33 sarah-laptop gconfd (sarah-4626): starting (version 2.14.0), pid 4626 user 'sarah'
Oct  2 17:19:33 sarah-laptop gconfd (sarah-4626): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  2 17:19:33 sarah-laptop gconfd (sarah-4626): Resolved address "xml:readwrite:/home/sarah/.gconf" to a writable configuration source at position 1
Oct  2 17:19:33 sarah-laptop gconfd (sarah-4626): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  2 17:19:33 sarah-laptop gconfd (sarah-4626): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  2 17:19:33 sarah-laptop gconfd (sarah-4626): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  2 17:19:38 sarah-laptop gconfd (sarah-4626): Resolved address "xml:readwrite:/home/sarah/.gconf" to a writable configuration source at position 0

Also, specs on the computer: 
Processor: Pentium IIIM
Video card: ATI Mobility RADEON

Thanks!

---

### Post by sarahsiggy on 2006-10-04
Fixed it!  I just decreased screen resolution . . .:D

---

