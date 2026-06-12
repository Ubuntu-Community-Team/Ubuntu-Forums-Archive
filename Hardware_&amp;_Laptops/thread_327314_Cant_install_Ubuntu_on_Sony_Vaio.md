---
title: "Cant install Ubuntu on Sony Vaio"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by talbain on 2006-12-29
I have a Vaio PCG-R505 with a CD/DVD Drive in it's docking station and it seems like Ubuntu wont install, funny thing is that the Ubuntu live CD does boot and shows me the menu, so i proceeded but after a while the CD drive stops reading, i also tried the alternate disc but then it says it cant find a driver for the cdrom and gives me some alternate drivers to choose from, tried them all to no avail, did anyone have this kind of problem? i couldnt find many useful threads about this...

---

### Post by adriantry on 2006-12-29
> **talbain said:**
> I have a Vaio PCG-R505 with a CD/DVD Drive in it's docking station and it seems like Ubuntu wont install, funny thing is that the Ubuntu live CD does boot and shows me the menu, so i proceeded but after a while the CD drive stops reading, i also tried the alternate disc but then it says it cant find a driver for the cdrom and gives me some alternate drivers to choose from, tried them all to no avail, did anyone have this kind of problem? i couldnt find many useful threads about this...

I had the same experience on my Sony Vaio when trying to install Edgy (6.10).

I had no problem at all when installing Dapper (6.10). Perhaps you could try that.

I've meant to getting around to using the alternate install CD, but ended up reinstalling Dapper. If you want Edgy rather than Dapper, maybe you could try installing that way.

Adrian

---

### Post by talbain on 2006-12-29
Yes, i have tried to install edgy using the alternate disc also, but didnt work... well its good to know dapper does work, thanks for the info, if there is no other workaround then i'll do that, thanks again. :)

---

### Post by valhalla_beaver on 2007-01-05
I had the problem where Edgy Eft alternative install cd booted up but couldn't detect the cdrom on the dock. Solution was to use "cdrom" module and the device /dev/scd0 at the stage where hardware is being detected. Everything installed fine after that.

The cdrom device connects to the laptop by firewire. Apparently the sbp module enables the cdrom module to work; the cdrom device itself, as for every device connected to the computer, in /dev. If you go to the shell prompt, "ls /dev" will show you which devices are recognized. Note there is no "cdrom" device, hence it must be the "scd0" device.

If you plan on using a pcmcia linksys network card, also possible to set it up using ndiswrapper and the windows INF device driver.

Cheers

---

### Post by craig.o on 2007-04-20
> **valhalla_beaver said:**
> I had the problem where Edgy Eft alternative install cd booted up but couldn't detect the cdrom on the dock. Solution was to use "cdrom" module and the device /dev/scd0 at the stage where hardware is being detected. Everything installed fine after that.

Cheers

Thank you.  This worked like a charm for me on:

kubuntu 7.04 alternate,
sony vaio r505-jlk 192MB RAM

regards,
-Craig

---

