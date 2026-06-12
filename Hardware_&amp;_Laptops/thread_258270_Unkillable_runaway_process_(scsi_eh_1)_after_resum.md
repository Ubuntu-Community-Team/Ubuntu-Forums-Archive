---
title: "Unkillable runaway process (scsi_eh_1) after resume from standby"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by Kensey on 2006-09-15
Today I noticed my laptop (Dell Latitude D610) CPU temperature spike after I resumed it from standby (I noticed it after installing kernel updates but before rebooting, but have no idea if that's related).  Usually this indicates a runaway process -- this time the culprit was scsi_eh_1 (usually it's gnome_cups_icon).  Of note is the fact that I had to go to a terminal and run top to find this out -- System Monitor didn't display the process at all.

This was the first time I'd seen this process running away with my CPU and I was unable to kill it via either -HUP or -9.  I ended up having to reboot and even then the laptop hung at "Will now reboot" and I ended up having to force-power-off with the power button to get it to shut down.

As of right now, post-reboot, the CPU is fine.  There are two scsi* processes, scsi_eh_0 and scsi_eh_1, but neither is active (their status is S<, meaning they're in interruptible sleep but high priority).

Is there a way to avoid scsi_eh_* running away with my CPU again?  I can deal with gnome_cups_icon doing it on occasion because a HUP takes care of it, but I don't want to have to reboot my laptop all the time to get the CPU down from 70 C to a normal 40-50.

Is suspend-to-RAM known to cause issues like this on Dell Latitude D610s?  It seems like runaway processes always happen after I resume from standby.

---

### Post by digidocs on 2006-09-17
I have the same issue coming back from suspend on my D620...
-DC

---

