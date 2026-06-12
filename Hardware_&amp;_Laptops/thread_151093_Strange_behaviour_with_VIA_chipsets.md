---
title: "Strange behaviour with VIA chipsets"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by rklauco on 2006-03-27
Hello.
I successfuly installed Ubuntu on multiple systems.
Later these days I found a strange problem.
I have a "file and video" server running ubuntu with KM400 chipset from VIA (MSK K7M4 mainboard).
When I use reboot in gnome or restart in shell, I can see how services are shuting down, but the system wont restart.
I get only message Restarting system and the system stops on this. It is correctly writen in logs etc.
The same behaviour occures on other MSI board with VIA chipset, but this time KM800 (board in Midas800 PC, K8M800 board).
Also, the restarting process ends at the message.

And one more error on the KM400 chipset.
After reboot, sometimes, the sound card is not working. Everything seems to be OK, modules are loaded, no problem in dmesg or logs, I can see volume controls in gnome and console, but I can't hear any sound. After few restarts, everything is OK.

Thanks in advance for any tips/links.

---

### Post by LucasLinard on 2006-03-27
I had the same sound problem (I THINK). THe Master VOlume at eht sound mixer was somehow 0 and mute.

---

### Post by rklauco on 2006-03-27
Well, for me the volume is OK.
That's why I wrote that every volume control seems to be just fine...
I checked volume control using shell and using the gnome volume control and everything was set OK, but the sound was muted and only restart seems to be helping...

---

### Post by philipgm on 2006-04-06
I had the same restart behaviour, but the problem went away when I moved to a more recent kernel.

---

### Post by rklauco on 2006-04-06
[QUOTE=philipgm]I had the same restart behaviour, but the problem went away when I moved to a more recent kernel.[/QUOTE]
I have the most recent 5.10 kernel available and the behaviour ocures still.
And, on the other machine, there is 2.6.12-9...

---

### Post by philipgm on 2006-04-08
I installed the 2.6.14-ck1 kernel following the HOW-TO in these forums. The latest kernel in the repos had that restart behaviour me, that is the version you quote. You could install Dapper Drake which will take you to the 2.6.15-20 kernel.

You should remember that the repos for Breezy keep the stable releases so tend to be somewhere behind the current kernel.

Phil

---

