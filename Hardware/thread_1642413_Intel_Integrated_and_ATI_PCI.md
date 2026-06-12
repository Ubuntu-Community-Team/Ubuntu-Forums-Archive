---
title: "Intel Integrated and ATI PCI"
date: 2010-12-10
forum: Hardware
---

### Post by Silly2All on 2010-12-10
Hi, I'm very new to this Linux environment.  I have Ubuntu 10.10 set up.  However, it won't detect the ATI graphics card that is installed.  I does recognize the integrated Intel Graphics card.  This is the printout for lspci -v:

0a:09.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Rage 128 AIW
	Flags: bus master, stepping, fast Back2Back, medium devsel, latency 66, IRQ 3
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=64M]
	I/O ports at 2000 [disabled] [size=256]
	Memory at d4200000 (32-bit, non-prefetchable) [disabled] [size=16K]
	[virtual] Expansion ROM at d4220000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: aty128fb

How do I use this information so that I can get the graphics card recognized at startup?

Thanks so much!
Tan

---

### Post by cascade9 on 2010-12-11
I'd have a look in your BIOS and see if you can get the BIOS to initalise the ATI video, not the onboard intel video.

---

### Post by WinRiddance on 2010-12-11
A lot of mainboards have the ability to disable the integrated graphics chip either directly on the board itself with a jumper setting (the manual will show you where), or within the bios settings, where you'd select the option of NOT using the built-in graphic chip at all (by disabling that feature).

Don't know about Ubuntu but older Windows Operating Systems wouldn't recognize a new graphic card alongside an onboard chip either ... unless the built-in graphic chip was disabled first. That's because by default the onboard hardware is normally recognized during the initial post, and obviously it's not (commonly) possible to run two graphic chips at the same time.

Once you disable the built-in chip, go ahead and save your settings, power off completely, and then power the system on again after a couple of minutes. More than likely the new graphic chip from the new card on your computer will then be recognized. If not, you may have to search for hardware drivers by going from your Ubuntu menu to SYSTEM, then ADMINISTRATION, and finally HARDWARE DRIVERS. Don't do that though until you've made sure that the onboard chip has been disabled. Good luck! ;)

---

### Post by cascade9 on 2010-12-12
> **WinRiddance said:**
>  If not, you may have to search for hardware drivers by going from your Ubuntu menu to SYSTEM, then ADMINISTRATION, and finally HARDWARE DRIVERS. 

In a lot of cases this works, but not with an ATI Rage. They are a long, long way out of suport from ATI/AMD, the only drivers that will work on that card are the open source drivers.

---

