---
title: "Video Capture Card Stops Hotplug Subsystem at Boot"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by polo_step on 2005-07-21
Yeah, I'm trying once again to get a working webcam going and according to the various pages, this FlyVideo LR51 card with a Bt879 chip is supported with drivers in the kernel. A Sanyo camera plugs into it.

I plugged the card into a PCI slot and booted up, but "Hotplug Subsystem" seemed to freeze during bootup.  After a minute or two, I hit reset.  Made no difference, still wouldn't boot up.  I pulled the card and the system booted properly.

Any thonghts on this?  Am I doing something wrong?  Does it take much longer for hotplug to do whatever it does if there's new hardware?

As always, thanks for any help.

---

### Post by black hole sun on 2005-07-22
[QUOTE=polo_step]Yeah, I'm trying once again to get a working webcam going and according to the various pages, this FlyVideo LR51 card with a Bt879 chip is supported with drivers in the kernel. A Sanyo camera plugs into it.

I plugged the card into a PCI slot and booted up, but "Hotplug Subsystem" seemed to freeze during bootup.  After a minute or two, I hit reset.  Made no difference, still wouldn't boot up.  I pulled the card and the system booted properly.

Any thonghts on this?  Am I doing something wrong?  Does it take much longer for hotplug to do whatever it does if there's new hardware?

As always, thanks for any help.[/QUOTE]
 sudo rm /etc/rcS.d/S40hotplug
sudo rm /etc/rcS.d/S41hotplug-net

These commands stop hotplug from starting up.

---

### Post by polo_step on 2005-07-22
[QUOTE=black hole sun]sudo rm /etc/rcS.d/S40hotplug
sudo rm /etc/rcS.d/S41hotplug-net

These commands stop hotplug from starting up.[/QUOTE]
What is the Hotplug subsystem and what is it doing when this happens?  Should the card then self-install, and afterwards Hotplug be reactivated?

Thanks for any clarification.

---

### Post by black hole sun on 2005-07-22
[QUOTE=polo_step]What is the Hotplug subsystem and what is it doing when this happens?  Should the card then self-install, and afterwards Hotplug be reactivated?

Thanks for any clarification.[/QUOTE]
 I have no idea :D Hotplug is supposed to configure devices that are added to an already-running system (eg, an iPod or in your case a webcam). For some reason it's hanging itself trying to configure your webcam. I'm afraid I can't help you with that :( , but at least I can help you get ubuntu back to useable state where you might be able to fix your problem.

---

