---
title: "laptop / acpi"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by xjas05 on 2007-02-18
installed edgy on my laptop.. on the main menu when you installed i added a "-no-acpi" and everything was good.. and then when i booted into my new install, the screen goes blank after about 5 minutes and everything just starts to turn off, hard disks and stuff... i even compiled a new kernel and disabled ACPI in the kernel...

---

### Post by DagMan on 2007-02-18
Have you tried 'sudo apt-get bum'
run bum as root and deselect acpi.  If it is still happening, also deselect apm.

If that doesn't work I can't help out other than to suggest also removing apm support in the kernel.

Also, see if the bios has options to toggle power management settings.

---

### Post by xjas05 on 2007-02-18
checked bios... it wasnt doing this when it was running on windows. theres no acpi or apm in bum, checked services, and startup and shutdown scripts

---

### Post by DagMan on 2007-02-19
Yeah you're right eh?  I just looked on my own machine and it doesn't find or doesn't allow editing of those services.

I wonder how safe it is to mess with though... if it's messing with things like the cooling fan.
If you want to give it another shot, try this
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I was actually looking for that yesterday and couldn't find it but remembered bum.
They are acpid and apmd.  Perhaps only one of them is the offender for you.

---

