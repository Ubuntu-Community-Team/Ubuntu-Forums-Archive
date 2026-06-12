---
title: "acpid scripts not called when resuming"
date: 2008-04-30
forum: Hardware
---

### Post by plaa on 2008-04-30
Hi,

I recently upgraded my xubuntu installation from Gutsy to Hardy on my Thinkpad T23.  I noticed the new Gnome Power Manager icon on the xcfe menu, and was pleasantly surprised that you could configure the actions so easily.  (I want my laptop to suspend when closing the lid - though the automatic backlight dimming options do not work for me.)

However, I had made a few extra configurations to /etc/acpi/resume.d, which set up my home network and mutes/unmutes my sound card (which otherwise won't work after resuming).  These no longer work on Hardy.  I tried adding a simple script that simply echo's a line to /tmp, and it was not run when resuming.

If acpid doesn't handle the events any more, how can one add scripts to be run when suspending/resuming?

---

