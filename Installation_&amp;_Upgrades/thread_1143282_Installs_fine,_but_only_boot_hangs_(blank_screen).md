---
title: "Installs fine, but only boot hangs (blank screen)"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Lhademmor on 2009-04-29
Hi all. I've recently got a new computer (w/ 64bit-capable Intel Core 2 Quad 2.4 GHz CPU) and tried to install Ubuntu on it both using Wubi (downloaded the 64-bit version) and a DVD (the 32-bit version I think), but the result is always the same:

The installation proceeds well and when I reboot I get to choose between Windows XP and Ubuntu, so I pick Ubuntu and I get the new, fancy thin progress bar. It loads all the way up to 100% and the screen blanks and... nothing happens! GNOME never shows up like it's supposed to.
I've tried waiting 30 minutes in case it was a problem with some slow processes, but even after 30 minutes the screen is still completely blank - the hard disk is even silent.

I have also tried booting in Safe mode and ACPI Workaround mode (whatever that is), but all in vain.

Do any of you have any idea what could be the cause of this? It's very frustrating to not even get any errors but only a blank screen...

---

### Post by upchucky on 2009-04-29
if you can boot in safe mode you should be able to use the command prompt, if true then the next step is to edit the xorg.conf and enter the screen settings manually.

did the live cd boot up to a graphical display before the actual install?
if yes then boot it again from the live cd and then look at the screen setting the live cd uses for the display, copy them down and enter then into the xorg.conf on the hard drive

I think the setting when booted from the live cd are in a temp file /boot/X11/xorg.conf if you cant find then then searching for graphic display posts the same as your system should find the right settings

---

### Post by Lhademmor on 2009-04-30
Okay.. I just tried booting from the DVD. Nothing happened.
Then I tried booting from the DVD in Safe graphics mode - and then I got all the way into GNOME!

I am currently in the process of (once again) installing Ubuntu using Wubi, to see if I can also get into GNOME using Safe graphics that way.

Also, there was no /boot/X11/xorg.conf and I didn't really understand the last part of your reply.

By the way, when I tried booting from the DVD into safe graphics mode with 'acpi=off' I noticed an error message saying something along the lines of 'Warning: Your PnPBIOS caused a fatal error. Attempting to continue'. But it booted into GNOME fine so I have no idea if it's related to anything.

Bottom line: Safe graphics mode from the DVD seems to work (both with acpi=on and =off apparently).

---

### Post by Lhademmor on 2009-04-30
Never mind. I booted from the DVD into safe graphics mode and installed. Once installed everything seemed to be working fine.

A bit of weirdness though: At the end (90%-100%) of the installation process the installer seemed to 'fall asleep' a couple of times where the DVD and the harddrive would go silent and 'pause' the installation - but once I kickstarted the DVD again (e.g. by opening some menus or Firefox or whatever) the system woke up and continued the installation. Very weird, and I'm thinking that this may have been related to the original problem as it was also characterized by non-existing DVD and harddrive action.

---

