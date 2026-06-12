---
title: "How to make something happen on APM suspend?"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by sb73542 on 2005-11-25
Hi, 

I have Breezy on a Thinkpad 600, which works fine with APM suspend/resume.  However, with this laptop, I need to run a script to make my modem work and to restart hotplug every time I resume from a suspend-to-RAM.  How can I make the system do this automatically?  There is a section in /etc/defaults for ACPI, which would let me specify the "services to restart after suspend", but this doesn't affect APM's behavior.  I tried adding a script to the /etc/apmd/suspend.d/ directory, but it doesn't run it.

In addition, I need to make cardmgr "Eject" my pcmcia cards before it tries to suspend, otherwise it refuses to even start the suspend process.  How can I eject PCMCIA before suspend, and re-insert it after resuming, without restarting the PCMCIA service?

Thanks for your help!

---

### Post by sb73542 on 2005-11-27
Bump

---

### Post by gotaserena on 2005-12-20
check /etc/apmd/events.d/alsa, copy and modify it so it (re)starts the hotplug service. Then add symlinks (with the appropriate numbers) to ../suspend.d/ **and** ../resume.d/

By the way, what was the symptom of hotplug failing? My tp600 starts blinking the screen and caps lights everytime I resume... :(

---

### Post by ranf on 2005-12-20
[QUOTE=sb73542]
In addition, I need to make cardmgr "Eject" my pcmcia cards before it tries to suspend, otherwise it refuses to even start the suspend process.  How can I eject PCMCIA before suspend, and re-insert it after resuming, without restarting the PCMCIA service?
[/QUOTE]
cardctl eject
cardctl insert

---

