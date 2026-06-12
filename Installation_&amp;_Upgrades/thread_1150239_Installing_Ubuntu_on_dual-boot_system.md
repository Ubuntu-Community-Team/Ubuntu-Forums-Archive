---
title: "Installing Ubuntu on dual-boot system"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by epp on 2009-05-05
I have a desktop (Compaq Presario) which was dual-boot with Windows XP and (what was) Mandriva Linux.

Upon attempting to install the new version of Mandriva, the installation media (a regular installer CD and also a separate LiveCD) both failed to work as intended.  The regular installer displayed I/O errors while trying to copy the packages from the CD and the X server loaded from the LiveCD kept crashing.  Windows XP boots up fine though and there are no problems with Windows.

Here is the dilemma.  When I installed Ubuntu 9.04 on my laptop, which also had Mandriva previously installed (Linux-only on this, no Windows), upon logging into the account for the first time after the installation (using same login name as used under Mandriva), I had a corrupted GNOME desktop.  Both the top and bottom panels were empty (no menus, clock, etc.) and just below the top panel, there was a short 1/2" long panel displaying only the Terminal icon.  The only way to fix this, was to reinstall Ubuntu while also formatting the /home partition the second time around, losing all of the data on it (which was not much).

On the desktop, the /home partition has a lot more data which currently cannot be accessed due to the failed Mandriva installation.

Is there a way to successfully install Ubuntu on this desktop, saving the data in /home while also not corrupting the GNOME desktop upon first login?  If the results would be the same as what I experienced on the laptop, then it would be best to simply leave Windows on the desktop and not bother with Linux on it.

The desktop's specs are:

CPU:  AMD Athlon 600 MHz (i686 architecture)
RAM:  512 Mb (maxed out)
Video:  S3 Savage-based video card (8 Mb video RAM on the card)

Thanks in advance for any advice and/or suggestions.

---

### Post by cariboo on 2009-05-05
The big problem, is the video card, as S3 doesn't support Linux very well, if your /home partition is seperate you should have no problem. I would suggest you always backup your important data before doing anything.

---

### Post by epp on 2009-05-09
When I installed Ubuntu (since replaced with Xubuntu) on my laptop, the GNOME desktop settings from the Mandriva Linux setup, resulted in the corrupted desktop.  The only way to fix this was to reformat /home and start fresh again.  What was in /home on the laptop was easily replaced.

I'm afraid that if I tried to install Ubuntu on the desktop system in question, I will end up with the same result...

---

