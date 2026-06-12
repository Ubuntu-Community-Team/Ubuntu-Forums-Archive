---
title: "Slow bootup/shutdown/suspend, how to remedy?"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by daij on 2005-09-15
I just did some timing experiments on my Acer 3212WXMi (PM 1.7, blahblah).
ABIOS is configured with the Fast-Boot option, GRUB boots default option with a timeout of 0 (immediately), and I'm automatically logged in gdm. These are my (devastating) results:

Suspend-to-RAM (sleep): ~10s
Resume-from-RAM: ~8s
Suspend-to-DISK (hibernate): ~54s
Resume-from-disk: ~58s

Boot from power-on-button pressed to usable gnome (no startup apps, but a few  applets): ~1m 38s
Shutdown from "Shut Down"-option selected in gnome: ~40s

This is with a minimal amount of startup services (ie. no apache, database, mail), and with the wireless network adapter using a prerecorded dhcp-lease.

These results are embarassing compared to Win XP, which is a lot faster on my computer in all cases, not to mention OSX which has almost instant sleep/resume (but that's another world i guess...).

It would be very interesting to hear from you about timings on similiar hardware, and any options/efforts made to reduce them.

--
Regards.
daij

---

### Post by mlomker on 2005-09-15
Linux didn't really even have power management at all until kernel 2.6, afaik.  Everything related to laptops is still fairly recent.

If someone wanted to spend the money/hire programmers to do the work then I'm sure it'd get done.  Microsoft has $billions to hire the best programmers.

---

