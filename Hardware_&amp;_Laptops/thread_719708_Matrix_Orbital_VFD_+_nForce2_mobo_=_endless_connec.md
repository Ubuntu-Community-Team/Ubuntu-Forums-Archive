---
title: "Matrix Orbital VFD + nForce2 mobo = endless connect/disconnect!"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Big_Rog on 2008-03-09
I'm trying to get my VK202-24-USB display connected to my HTPC, but it won't stay connected.  The display connects to my main rig (nForce520 board) and has been able to connect to the htpc board under Windows in the past.  dmesg shows connect/disconnect looping with incrementing connection numbers.  I've tried removing the ehci module to see if it's related to USB2.0, but it does the exact same thing with that module unloaded.  The recognized drivers seem to be the restricted nvidia (fxusb?) using a FTDI chip for USB interface.  The exact same drivers are installed on my main rig and don't seem to cause problems.  I've read a few launchpad bugs about nforce2 kernel issues with USB, but didn't find anything relevant.  The only USB->Serial solutions i've found all refer to interference from brltty, but it's not installed on the HTPC at all, and doesn't show in the dmesg log: it does on those solutions.  Hmm, looking at the pcb for the display itself, the FTDI chip is on the display, which looks to be the converter from serial (the normal connection for these displays) to USB.  I found a post about external drives that had a similar problem that was solved by using a powered external hub, but i don't have one of those.  The USB port is on the back of the mobo, so it should have the full 5V supply.  There isn't a jumper for dis/en-abling power to the USB ports like i've seen on some boards. dmesg and lspci -vvnn attached.

Setup:
 * Mythbuntu 7.10 (2.6.22-14-generic kernel)
 * Albatron KX18D ProII nforce2 motherboard --uses nforce2 SPP (ultra 400) northbridge, MCP-T southbridge
 * Matrix Orbital VK202-24-USB VFD

---

### Post by Big_Rog on 2008-03-10
Hmm, seems that the issue really is power related.  I double checked the manual for the proper power cable (unmodified floppy) and plugged it in.  Default welcome screen lit up like a champ!  Reverted to the Feisty driver (as recommended on launchpad) though screen corruption persists...

---

