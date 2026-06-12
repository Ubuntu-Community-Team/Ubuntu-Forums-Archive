---
title: "resume from hibernate and suspend raid card issue"
date: 2012-10-28
forum: Hardware
---

### Post by NetGO on 2012-10-28
Spent long time to identify my resume issue. Hibernate and suspend works fine but resume fails.
 
Installed HighPoint 2760A raid card and installed rr276x.ko module compiled from linux souce code by the mfr.
 
System disk is connected to this raid card and boot from raid1. Because this card support sata3.
 
Tested on console mode. 12.10.
 
After hibernation, when resume, machine is up but it spits out IO error to Hard drive from mdadm and system starts to generate continous beep sound - I am not sure this sound comes from 2760A or motherboard. So I had to cold boot.
 
Tried to add this module to unload first, but pm log says that module is in use so it cannot unload before going suspend. So I removed this line from config.d.
 
Can someone help me? Maybe I need to add some hook to resurrect this card during resume?
 
Any idea is welcome.
 
Thanks in advance.

---

