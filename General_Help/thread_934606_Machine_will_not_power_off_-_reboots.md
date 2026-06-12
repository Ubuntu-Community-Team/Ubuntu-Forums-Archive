---
title: "Machine will not power off - reboots"
date: 2008-09-30
forum: General Help
---

### Post by aed on 2008-09-30
I have installed Ubuntu Server 8.04 onto a clean system using an Asus P5PE-VM.  My problem is that when I attempt to shut down Ubuntu it does shutdown but does not power off, but reboots and starts Ubuntu again.

I have reset the BIOS back to defaults om case this was the issue.

This happens if I use 'sudo shutdown -h now' or 'sudo halt'.

Any ideas?

---

### Post by ThaddeusW on 2008-09-30
Sounds like some weird APM bug with your motherboard. Dig into the BIOS and look for the APM settings and play with those. Have you checked the ASUS website for BIOS updates? Many times the first revision of a BIOS has bugs so always check for patches.

---

