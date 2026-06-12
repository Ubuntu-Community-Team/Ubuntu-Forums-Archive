---
title: "Printing is broken - how do I fix?"
date: 2009-06-24
forum: Hardware
---

### Post by reuben on 2009-06-24
I have an exceptionally annoying printing problem. This happened on both KDE and Gnome.

The issue is that when I reboot, my printer configuration is somehow invalidated, such that printing no longer works the next time I log in. I have to delete and re-add the printer via the UI to re-enable it.

This is a network printer (an HP 8150). Using either kde-printer or gnome-printer, I add the printer (it's detected fine). I print. All is good. I reboot. I try to print. The printer applet shows the job in the queue as "processing", as does lpq. Hours pass. I give up, go into the UI, delete and re-add the printer. I send through a new print job. It works. Rinse and repeat.

I have a bug open on this ([https://bugs.launchpad.net/gnome-print/+bug/368977](https://bugs.launchpad.net/gnome-print/+bug/368977)) but like much on launchpad it's getting zero love from anybody connected to the projects. Anybody have ideas for permanent workarounds?

---

### Post by prshah on 2009-06-24
> **reuben said:**
> 
This is a network printer (an HP 8150). Using either kde-printer or gnome-printer, I add the printer (it's detected fine). I print. All is good. I reboot. I try to print. The printer applet shows the job in the queue as "processing", as does lpq. Hours pass. I give up, go into the UI, delete and re-add the printer. I send through a new print job. It works. Rinse and repeat.

Is your printer having a fixed IP, or a dynamic IP?

---

### Post by reuben on 2009-06-24
Ah interesting, I hadn't considered that. It's dynamic, but I'm not rebooting the router at the same time as the computer (or, actually, ever). 

Also, the gnome-printer applet shows that the printer is "on" when I power it up, even if it's unprintable to, so I know that it's still being detected.

---

### Post by prshah on 2009-06-24
> **reuben said:**
> 
I know that it's still being detected.

Can we have a look at your /var/log/lpr.log (taken after a successful print _and_ a failed print cycle).

---

### Post by reuben on 2009-06-26
Nothing in /var/log/lpr.log on the failed cycle. 

lpq reports:

barge is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  reubenf 90      NMFL 4506 - Request for Transcr 164864 bytes
1st     reubenf 91      Converted from 1097#_2006101115 98304 bytes


AH! It _is_ getting a different IP each time.

"Not working" -- Device URI is: hp:/net/HP_LaserJet_8150_Series?ip=192.168.1.6
"Working" -- Device URI is: hp:/net/HP_LaserJet_8150_Series?ip=192.168.1.2

But, why would lpq see it as being "ready and printing" (above) when it has the wrong IP? That seems like the core of this bug. I will edit my router to make this static for now.

---

