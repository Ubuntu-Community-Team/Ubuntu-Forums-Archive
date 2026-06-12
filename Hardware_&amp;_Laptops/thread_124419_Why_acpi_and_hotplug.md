---
title: "Why acpi and hotplug?"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-02-01
I hope I get some clarification here. I NEVER knew what acpi, apmd and hotplugd where for. Both on my iBook & my desktop machine (AMD64) I've removed acpid, apmd, and hotplug from the init scripts, rebooted (it boots a little faster) and the whole system behaves EXACTLY the same. The screen turns of, the laptop goes to sleep, USB devices get detected correctly, plugging the network cable in or out is detected just fine, the CPU slows down when not used, the HD spins down when not used ... so WHAT are acpi and hotplug actually doing??? What kind of hotplug devices does hotplugd control if not USB devices? Why is all this acpi & apm stuff loaded when all power management behaviour is exactly the same without them?

Can someone please clarify this? On my previous Gentoo system I also had a very sophisticated udev & power management config, and I also never used any of these daemons there. So what are they doing??

Tom

---

