---
title: "sounds problems"
date: 2008-08-03
forum: Hardware
---

### Post by asmugone on 2008-08-03
OK the sound was working untill my father decided it wasnt loud enough, not knowing anything about ubuntu he went into the bios disabled the onboard sound and then stuck in a ancient pci soundblaster, when that didnmt work he proceeded to tell me to fix it. I restored bios defaults and got no love, ubuntu said no audio device detected when i clicked on the sound icon, I formatted the drive and reinstalled ubuntu from the disc, no love, worked before dont know what going on now.

sudo lspci -v returns this for the sound

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: nVidia Corporation Unknown device cb84
	Flags: 66MHz, fast devsel, IRQ 18
	Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

the sound file is already built into the kernel and I treied modprobing the driver and it inserts but I still cant get the sound to work!!!!

Can anyone give me some help here?

system is a 2.5 DUAL Core amd on a elite group motherboad gefrce7050m-m

would really appreciate some help either getting onboard sound to work or this antiquated soundblaster pci card.

---

### Post by asmugone on 2008-08-03
bump

---

### Post by asmugone on 2008-08-03
ok, I now have the ancient soundblaster in did a fresh install and it didnt even detect the thing, also im reading that sound problems with this board the geforce7050m-m is very common even in windows so......

can anyone give me any help here?

---

