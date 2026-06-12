---
title: "Keyboard REALLY slow to initialize on HP dv2000t w/ Lucid 10.04"
date: 2011-05-09
forum: Hardware
---

### Post by mmiller7 on 2011-05-09
I'm having a problem with a new Ubuntu install and I'm not sure where to begin troubleshooting it. I've searched the forums and found similar issues (like the exact reverse of my issue) but nothing that seems to describe my problem.
 
When Ubuntu boots, it takes about 30-60 seconds before the internal laptop keyboard will respond. An external USB keyboard works instantly, as does the touchpad but the internal keyboard just won't do anything (even CAPS-LOCK) for the first minute.
 
Any ideas?
 
 
Before you ask a million questions, here are a few things I ran across searching that will hopefully give you an idea of what I tried.
**When did it start?** After I ran update-manager for the first time.
**Did it ever work correctly?** Yes, with the live-CD and the first time I booted before updates.
**Did I try the old kernel after the update?** Yes, but since the update it happens with both 2.6.32-28 and 2.6.32-31 kernels.
**Does an external keyboard work? **Yes, a USB keyboard works perfectly.
**Is the built-in keyboard USB or PS/2? **[COLOR=darkred]I don't know.[/COLOR]
**Does it work after sleep? **Yes, it works immediately resuming from hibernate. Sleep is still not wanting to work quite right so I don't know about that.
 
_Specs_:
Ubuntu Lucid 10.04.2
Dual-boot with Windows 7 x86 Professional (which works perfectly)
HP dv2000t
Intel Core2 Duo T5600
Intel Graphics Media Accelerator 945
Intel 3925ABG Wireless
HP Bluetooth (no idea what chipset)
 
Boot drive is 32GB "AData" 533x CF card in CF-SATA adapter
 
extra kernel parameters: "pci=nomsi" in an attempt fix a SATA I/O error resuming from sleep

---

### Post by mmiller7 on 2011-05-10
bump?

---

### Post by mmiller7 on 2011-06-13
bump again?  Nobody?

---

### Post by mmiller7 on 2011-10-28
Bump again?  Any ideas?
 
I just tried installing Ubuntu 11.10 and it has the same exact issue, internal keyboard won't work for the first minute or so.

---

