---
title: "Input device freeze when rebooting from Windows on Compaq laptop"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Dynaflow on 2007-12-30
I got the last $300 Compaq Presario C706NR at the only Fry's in Oregon on Black Friday.  One month later, I think I finally have this beast tamed.  ALSA has been rebuilt, the hard-drive's load-cycle suicide attempt has been been taken care of, and sundry other weirdnesses have been resolutely quashed -- but for one.

I'm keeping the laptop as a dual-boot machine because, in theory, as long as I don't completely take Windows off the hard drive, I'm not technically voiding the warranty, and even if I am, I can just back-up my files, delete my Linux partition, and restore the Windows MBR before bringing CompaqOfDoom in for service.

I occasionally log into Windows Vista to keep it updated and to do things like pay a traffic ticket at a court website that  **will** bounce anyone trying to check or pay tickets online who is not using IE (good work, San Mateo County, you got my money *and* my pride).

The problem crops up when I reboot the machine to return to Gutsy.  I have control of the keyboard and touchpad from GRUB up through the GDM log-in screen, but once I log into GNOME, all input devices become totally insensitive.  No response from the keyboard or touchpad whatsoever.  I can't even CTRL-ALT-BACKSPACE out of X.  The only way to solve the hardware freeze is to do a power-off with the power button and then boot the machine back up.

This is only occurring when I've been in Windows and then reboot to go into Linux via GRUB.  The problem is reliably reproducible (it happens every time, without fail) and it's also happening on my friend's dual-booting, Gutsy/Vista laptop, which happens to have been the second-to-last $300 Presario at that same Fry's where I got mine.

I suspect it's a problem at the hardware or BIOS level, but I have no idea where to start looking.  Can anyone offer some insight on this?  I'm using the 2.6.22-14-generic kernel, and the problem predates my implementation of Ubuntudemon's "ugly fix" for the hard drive and my rebuilding of ALSA to the latest version to deal with my HDA Intel-caused sound problems.

---

### Post by Dynaflow on 2008-01-02
[Bump.]  *Somebody* must have a guess...  :mrgreen:

---

### Post by Dynaflow on 2008-01-10
I'll give this post one last chance...  [bump]

---

