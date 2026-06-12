---
title: "Use LiveCD graphics settings on upgraded Jaunty install"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by urschrei on 2009-04-26
I upgraded from 8.10 to 9.04, with disastrous consequences for my X server settings (using ATI Radeon Mobility 3200)

I've uninstalled the fglrx driver using the script in /usr/share/ati, and reset my xorg.conf to its defaults, but I still get a hang at boot (seems to happen immediately after the DAMAGE module is loaded)
However, if I boot from the LiveCD, everything looks great, and boots perfectly.
How can I check that the ATI proprietary drivers definitely aren't being loaded/referenced? Is it possible that xorg is trying to load a proprietary module, and thus hanging?
Ideally, I just want to clone the LiveCD graphics settings onto the existing install, as they appear to work perfectly. Any ideas as to how I might go about this?

---

