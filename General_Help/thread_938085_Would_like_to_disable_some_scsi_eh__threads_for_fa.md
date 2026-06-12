---
title: "Would like to disable some scsi_eh_* threads for faster boot"
date: 2008-10-04
forum: General Help
---

### Post by engocoka on 2008-10-04
For fun, I am profiling and speeding up my boot process for my Ubuntu machine.  As you can see from my attached bootchart, the largest time eater is the modprobe process.  If I'm understanding it correctly it seems to be waiting on the khubd which in turn waits on the scsi_eh_* processes.  

I have 6 SATA ports on my motherboard, so I assume thats where the scsi_eh_[0-5] come from.  However, I'm only using 2.  I've tried disabling them in the BIOS, but it's an all or nothing switch.

I don't understand how these are started, or if they are even necessary for the ports that aren't in use.  Is it possible to disable some of them to ultimately shave off another 1.5 seconds from my boot time?

Thank you for your help!

---

