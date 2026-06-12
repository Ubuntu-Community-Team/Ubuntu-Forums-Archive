---
title: "suspend to ram + usb devices"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by dave9191 on 2005-07-15
Im one of the lucky few for whom the suspend to ram feature works "most" of the time. But it drains a lot more battery then windows in standby. And today I left my usb mouse plugged and during standy the mouse still lights up. So Linux isnt shutting down usb devices during standby, explaining why it uses more battery then windows. And I guess it might not be shutting down other things. Has anyone looked into this stuff before and is this being worked on with breezy ? 

Dave

---

### Post by toastedd on 2005-08-22
[QUOTE=dave9191]Im one of the lucky few for whom the suspend to ram feature works "most" of the time. But it drains a lot more battery then windows in standby. And today I left my usb mouse plugged and during standy the mouse still lights up. [/QUOTE]

I think that's because your Suspend to RAM is not working properly... not that Ubuntu is not turning off your USB devices.

You're using ACPI right, and not the outdated APM? (make sure no acpi=off in your grub config). APM is a last resort.

---

### Post by dave9191 on 2005-08-23
Im using ACPI. but its just not working properly. Although its partly a cool feature, I can charge my iPod when the laptop is in suspend. But I wish I could turn the USB devices off in a suspend script. 

Dave

---

### Post by coaxx on 2005-10-03
It looks like I have some similar problems here with STR/acpi. I have a Logitech USB Laser mouse and a Benq DVD -R/RW external writer connected to my USB ports. Going to standby works well. Coming back there is a shotz outage of about 10sec alreaedy seeing the KDE desktop, then the mouse works again, but the writer does not. I have to unplug and plufg it to rework. Also: my settings for the different mouse buttons only work after pulling out the mouse an reinsert it.

Maybe someone couldt tell us a bit what happens during reinserting the usb devices. So we couldt do it automatically in /etc/acpi/resume.sh

thx!

---

