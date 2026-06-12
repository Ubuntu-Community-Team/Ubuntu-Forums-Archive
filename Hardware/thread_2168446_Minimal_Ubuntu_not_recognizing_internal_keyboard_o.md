---
title: "Minimal Ubuntu not recognizing internal keyboard on old Dell Inspiron 2600"
date: 2013-08-17
forum: Hardware
---

### Post by violinuxer on 2013-08-17
I have a VERY old Dell Inspiron 2600 laptop (1.3Ghz cpu, 128Mb of ram) that I recently decided to resurrect for use as a (semi)dumb serial terminal. I downloaded a mini ubuntu ISO of raring and installed the bare-bones ubuntu installation (a process which took all of 2 days :p). I installed and set up screen for use with an FTDI USB-serial cable that I have connected to my headless server. For the the first time in 4 years of using ubuntu (yeah Hardy!) the internal keyboard is the one thing that doesn't work.

Here's what's going on:

I ran through the installer, selected only the base system (no extra utils, services, etc) and when prompted, had it only install drivers for what was on the machine. It booted fine, loaded grub, and finally put me at a login prompt. However, I was unable to type using the internal keyboard. A USB wireless keyboard worked fine, but I could not get get the on-laptop keyboard to work...  Often it works when I manually select the kernel entry from the grub menu. 

Other than adding screen, all I've done is remove "quiet splash" from the commandline so I could read debug mesages.

Are there any kernel params that might help me out? Am I missing any packages? Can I rescan the peripherals (or is that impossible due to the fact that the keyboard is PS/2)?

Thanks so much for your help!

violinuxer

EDIT: A clarification: this computer is running a bare command line. No Xserver whatsoever.

---

### Post by TheFu on 2013-08-18
Does the BIOS see the keyboard?  I suspect yes.
Does **lshw** show the keyboard?  I see it connected to int9 on my physical machines.  Don't know if that is always shown or not.  Could be a list of motherboard BIOS capabilities.  I do know that VMs do NOT show it.

Sorry - I don't know.  I do run PS2 devices on a few systems here, but I've never tried with a minimal Ubuntu install.

---

### Post by TheFu on 2013-08-18
delete ... post error by the forum.

---

