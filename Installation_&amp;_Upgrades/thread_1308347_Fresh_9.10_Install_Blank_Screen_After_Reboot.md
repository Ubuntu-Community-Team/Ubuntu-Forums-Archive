---
title: "Fresh 9.10 Install Blank Screen After Reboot"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by jakj on 2009-10-31
I'm using standard 9.10 i386 installed (freshly-formatting the drive each time) on a Dell Dimension 2400 (Celeron, 512MiB RAM).

The installation CD works 100% in both installer mode and LiveCD mode. Reboot after installation, works fine. Get some stuff installed, configure dnsmasq/resolvconf/ufw, get updates, reboot, works fine.

Shut the machine off for a bit, turn it back on, Grub screen works fine, dimming/brightening Ubuntu logo loading screen works fine, screen goes completely black with no additional hard disk activity once it tries to fully get into X. Nothing I try works. Boot back into the LiveCD, works fine.

Started over. Wiped the drives and did a new fresh installation. Second verse, same as the first: Works for a while, eventually boots into blank screen instead of X.

9.04 worked fine. I didn't have to configure any video drivers at all to get it to work. It just worked. It just works in the 9.10 installer, and for a few boots after installing. Then it stops.

The screen is still powered on fully, not in error mode, but showing complete blankness.

I have already read the existing issues dealing with Dell computers and blank screens, but all of those are errors where either the installer won't even display correctly, or the fresh installation can't display at all. Mine does display...for a few boots. This clearly is not an issue of X being misconfigured on installation. The only thing I can think of is that something somewhere is getting updated after installation and messing up, but I can't see how that could be it either, considering that I can reboot a couple times after running Update Manager before it stops working.

Ideas? I hate Windows. Don't make me have to use it again.

---

### Post by jakj on 2009-10-31
As an update to this issue, I've been able to reproduce the behaviour reliably (though I haven't been able to diagnose it beyond guesses).  1) Every time I turn the machine off completely instead of simply rebooting, when it comes back up, it has the black screen, and continues to have it since the only way to reboot from there is hard power-down and up again.  2) If I boot from the LiveCD, and then immmediately reboot (removing the CD) onto the drive, it works without a blank screen.  So it has to be something that the installation CD is doing to initialize my hardware from cold start that doesn't reset on warm reboot, that isn't being done by the actual installed copy of the operating system.  Now, if Empathy would quit hard-locking the machine (Didn't think it still was possible to hard-lock the Kernel...heh), I wouldn't have to power down at all. (What kind of idiot designs a computer box without a reset switch? Dell, that's what kind. Bleh. Remind me to never buy a Dell again so long as I live.)  Hope that helps for tracking the problem down. Let me know if I can help with any further diagnoses.

---

