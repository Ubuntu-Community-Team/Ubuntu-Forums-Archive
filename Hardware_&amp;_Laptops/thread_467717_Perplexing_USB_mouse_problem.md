---
title: "Perplexing USB mouse problem"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by darkshadow88 on 2007-06-08
I just built a system for my sister yesterday and installed Feisty on it.  Everything works well except for the USB mouse.  When I boot the system, the usb mouse does not work (as this is an optical mouse, I can clearly see that there IS power going to it).  Unplugging it and plugging it back into any USB port (including the one it was originally plugged into) fixes the problem until the next boot.  I have been troubleshooting it for about eight hours and have learned the following:

-The problem persists regardless of whether USB mouse support is enabled in the bios.
-Other USB devices (including the keyboard) work fine
-It doesn't matter which USB port the mouse is plugged into (either the ones on the mobo or the case's USB ports); the problem remains the same
-The problem is the same even if all USB devices except the mouse are disconnected.

-Disabling the USB 2.0 controller in the BIOS (thereby making all ports behave as USB 1.1) REMEDIES the problem
-Unloading the ehci_hcd and ohci_hcd modules and reloading them remedies the problem ONLY IF I move the mouse while the modules are being reloaded.  If I do not move the mouse when I do this, the mouse remains stuck.
-Unloading and reloading the uhci_hcd module causes the problem to come back
-PS/2 mice work fine

My motherboard is a Gigabyte GA-945-S2 (945 chipset).

Does anyone have any suggestions?  I plan on picking up a USB to PS/2 adapter as a temporary workaround, but I would prefer a solution over a workaround.

---

### Post by darkshadow88 on 2007-06-08
I have just discovered that switching from the generic kernel to the 386 kernel also fixes the problem.

---

### Post by Go2doug on 2007-06-14
I believe I am experiencing the same problem. I use a Dell D820 laptop on the docking station. I have a Microsoft Intellimouse Explorer USB mouse plugged into a port on the docking station. Sometimes when I boot into Kubuntu 7.04, the mouse is not functional, even though it is lighting up. If I unplug the mouse and plug back in, the mouse becomes functional.

> I have just discovered that switching from the generic kernel to the 386 kernel also fixes the problem.

Should I do this, too? If so, how? Will there be any additional negative consequences?

---

