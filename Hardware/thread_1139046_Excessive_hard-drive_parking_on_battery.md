---
title: "Excessive hard-drive parking on battery?"
date: 2009-04-26
forum: Hardware
---

### Post by Null Actor on 2009-04-26
I just installed Ubuntu 9.04 on my laptop, and after a few installation bumps, things are going well, but there's one thing that worries me.  On battery power, I can hear my harddrive parking itself every 10-15 seconds sometimes as infrequently as one minute, but usually more often. 

This doesn't happen in windows, nor does it happen when I have my laptop plugged in. 

Laptop is a Dell xps m1530 with a T7250, 2gigs of ram, and an upgraded WD Scorpio Black 320gb harddrive.  

Install is brand new, bog-standard.  Don't know if happens in other builds, as this is the first Ubuntu I've tried on this laptop.

Any ideas/comments?

---

### Post by Aearenda on 2009-04-26
There have been many long discussions of this issue in previous versions of Ubuntu (search for Load_Cycle_Count in the forums if you have several hours to spare). In 9.04, when on battery, the drive is set to park the heads for protection in case of shock as the laptop is moved. When on AC, this is turned off. Some drives are noisier than others when parking or unparking. Some drives behave strangely even on Windows and on Macs, and there seem to be consistency problems between manufacturers on this.

You can modify this behaviour. If I understand it correctly, if you have laptop-mode enabled, you do this in /etc/defaults/acpi-support; otherwise, the settings in /etc/acpi/start.d/90-hdparm.sh (and the same name under /etc/acpi/battery.d - see also the resume.d folder) are used. 

The hdparm command sets parking off (with 254) or on (with 128 ) - depending on your drive, other settings may be useful.

---

### Post by Null Actor on 2009-04-27
Thanks for the input.  My harddrive has a built in free-fall sensor for parking the drive head -- so disabling this altogether should be fine.

---

