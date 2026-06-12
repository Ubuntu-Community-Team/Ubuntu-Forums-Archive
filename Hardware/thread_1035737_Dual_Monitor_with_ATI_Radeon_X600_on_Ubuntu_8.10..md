---
title: "Dual Monitor with ATI Radeon X600 on Ubuntu 8.10."
date: 2009-01-10
forum: Hardware
---

### Post by waeras on 2009-01-10
I know that this has been discussed earlier, and I've followed tips on this forum and several others to try to get my displays to work the way I want them to (ie. like in Windows.)

I have 2 wide screen monitors (One Asus VW195S, connected via VGA and one Videoseven L19WA, connected via DVI on the same Radeon card) and I use a 1440x990 resolution on each monitor. No problem at all in Windows, no problem at all in Ubuntu either if I just use one of the monitors. 

The problems began when I connected both. At first I only got picture on one of the monitors, so I quickly googled for help to install dual monitor setup. I followed some instructions, installed the latest ati driver (ati-driver-installer-8-12-x86.x86_64.run) and rebooted, figured I could use the ATI Catalyst Control Center to set up the second display and my desktop.

What happens when I reboot is the following though: I get an error that says something like this:


(EE) fglrx(0) Unknown EDiD Version 0
(EE) PreInit Dal failed
(EE) PreInit failed
(EE) Screen(s) found but none have a usable configuration

I then get the choice to start ubuntu in a low graphics mode. When I choose this I can't start Ati Catalyst Control Center since "no driver is installed or doesn't work" and that I should install the driver and congifure it with aticonfig.
I've tried reinstalling the driver, and tried different methods for dual screening, but I always get the same error on boot. 

Both monitors work btw, they're cloned and uses a 1280x1024 resolution. 

Does anyone know what I should do next to get this working? Any help would be greatly appreciated. 

Let me know if you need any more info too. 

Thanks

/waeras

---

