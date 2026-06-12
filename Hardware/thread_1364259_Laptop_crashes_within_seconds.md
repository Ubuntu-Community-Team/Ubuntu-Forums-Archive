---
title: "Laptop crashes within seconds"
date: 2009-12-25
forum: Hardware
---

### Post by guy0089 on 2009-12-25
I installed this ([http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)) last night and have been having problems. I'm not sure if it's related or just a coincidence. 
 
First some system info:
-I'm dual booting Windows 7 and Ubuntu (9.04)
-This is on a Gateway laptop T-1631
 
My laptop is shutting down "randomly". Basically this came up like this:
 
I run this script, fine. I restart my computer, fine. I log into Ubuntu, fine. Then the problem starts: when everything is nearly loaded, it shuts down (power just cuts out). I restarted it and the problem got worse. Everytime I restart, it shut down faster and faster, until it was shutting down just 11 seconds after start up (before even getting to grub loader to allow me to choose my OS). Even if I'm in the BIOS, it will still restart.
 
I'm not familiar enough with the workings of this script or computer hardware to know what is going on, but this never happened before and it happened right after running this script.
 
Another weird thing: sometimes it starts up in windows without restarting. What I have found is that if I manage to log onto windows, I'm home free. It won't restart (as far as I know), and I have had windows up and running for about an hour (normally this problem shows up within seconds, so this leads me to believe it will run indefinietly in windows).
 
Ideas?

---

### Post by IcarusR on 2009-12-26
If it happens from within the bios settings then that is not caused by OS.
Have you read through the thread on the script to see if anyone else has the same problem ??
How about posting on that thread, as the script author probably reads it regularly.

Have you tried uninstaling it ?

---

### Post by guy0089 on 2010-01-06
Sorry, I forgot to update this.  The problem worked out when I went in and reset the BIOS.  I'm not familiar with how an OS/software can affect the BIOS, but I feel like that package upgraded my BIOS to cause some issue, but when I reset my BIOS, it was fixed.

---

