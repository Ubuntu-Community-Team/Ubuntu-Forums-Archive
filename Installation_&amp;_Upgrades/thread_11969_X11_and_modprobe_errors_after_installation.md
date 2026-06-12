---
title: "X11 and modprobe errors after installation"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by yolint on 2005-01-20
I get this message although I'm not certaining its doing anything bad.
PCI: Cannot allocate resource region 4 of device 0000:00:02:1

Later on I get these.
modprobe: FATAL : Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko : operation not permitted.
modprobe: FATAL : Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko : operation not permitted.

Then I get X11 errors after I log in so I go right to a command line.

I'm pretty new to linux in general and this has me scratching my head so any help is appreciated. thanks

---

### Post by nightmorph on 2005-01-20
[QUOTE=yolint]I get this message although I'm not certaining its doing anything bad.
PCI: Cannot allocate resource region 4 of device 0000:00:02:1

Later on I get these.
modprobe: FATAL : Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko : operation not permitted.
modprobe: FATAL : Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko : operation not permitted.

Then I get X11 errors after I log in so I go right to a command line.

I'm pretty new to linux in general and this has me scratching my head so any help is appreciated. thanks[/QUOTE]


I have been having the exact same errors the past few days.

I've solved at least the X11 problem (with the exception of it recognizing my mouse) by switching to the base linux-386 kernel (2.4 I believe), and by booting the install cd in expert mode along with various combinations of **debian-installer/framebuffer=false** (this is key) and optionally, **noapic nolapic**. Oh, and another seemingly critical step is to include the option during the initial install process to allow for later configuration of base system before reboot; i.e., make possible running the second stage installer from within the first stage. My display is severely corrupted during this second stage configuration, but I am able to select the necessary options before reboot, and that gives me a working X system every time.

I still can't reboot my kernel after the initial installation & bootup; the first time, the fatal errors still appear, but at least the system moves past them. However, if you attempt to reboot your system after that, even if you make absolutely no changes to Gnome or any of its applications or modify any part of your system's configuration, chances are the next time you reboot, your system will still freeze at those error points.

Let me know if you're able to successfully reboot in spite of the modprobe errors. There are some instructions on this particular issue on this wiki page ([http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)), but the solution offered didn't fix the problem for me; my system still froze at the same place during boot, just without the error messages.

---

