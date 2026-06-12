---
title: "Hotplug / HAL Blacklist Problems (can't disable ehci_hcd)"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by JustRandomName on 2005-11-10
Hi,

I have a USB wlan card which uses the rt2x00 drivers. I have installed the drivers and everything is working fine.

The problem is that when ehci_hcd is enabled the connection drops (this is a known problem, it works GREAT on the ohci_hcd mod). The work around for this problem *should* be just to blacklist the ehci_hcd module.

I have done this and for some reason it still loads at boot, I can get full stability by:

sudo modprobe -r ehci
sudo modprobe -r rt2570
sudo modprobe rt2570

but it is annoying having to do this on every reboot.


I have looked in the "Device Manager" (GNOME Menu->System->Admin->Device Manager) and the reason that the USB 2.0 (ehci_hcd) is loaded is because on boot the USB card is detected, and the rt2570 is auto loaded.

I will probably be able to stop this by adding rt2570 to the blacklist menu, but won't that mean that hotplug (or HAL ?) will just ignore the rt2570 module and not bother loading it (even though I want it to load with the ohci_hcd mod).

I think I may have come up with a solution, but I am not sure on how to implement it, the solution is thus;

I have heard talk off runlevels(?) and from what I can gather at each runlevel at different stage of the boot process is performed. So if I can somehow blacklist the rt2570 from hotplug, but then renable it before the network config/time resolve then everything should be great right?

ANY advice would be ace,

Thanks for your time

---

### Post by JustRandomName on 2005-11-12
bump

---

### Post by SnEptUne on 2006-03-27
I have the same problem.  Did you have any solution yet?

---

