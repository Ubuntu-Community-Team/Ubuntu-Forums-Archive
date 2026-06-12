---
title: "Live CD: Wrong graphic card used."
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by Kyran on 2007-01-15
I'm trying to use the Live CD with a computer which as an inbuilt Intel 810 based GPU and a Geforce FX 5200 PCI graphic card attached to PCI slot 2.

The problem is that the cd is trying to use the inbuilt graphic card instead of the PCI one. I've tried attaching a moniter to each graphic card but the inbuilt one when Xubuntu loads has random pixels (not usable) all over the place.

Is there a command to force the Live CD to look for the graphic card at PCI 2? I've tried xmodule=nv but that wouldn't work unless the right graphic card was detected first.

---

### Post by aberry5555 on 2007-01-15
This option should be in your bios, not the live cd. Windows can figure out itself (via software after installation) which screen to use if you installed the card yourself, however if you want it to boot on the second card you should go in to your bios and check your options. Your intel 810 chipset is on-board so go and chech in the bios and find graphics options, you should be able to either set pci-2 as default or lock out the 810 chipset.

---

### Post by bigken on 2007-01-15
look for dissable on board grapics or boot from pci 1st ;)

in the bios

---

### Post by Kyran on 2007-01-15
No option in the BIOs. And the manual doesn't say anything about jumper settings.

---

### Post by bigken on 2007-01-15
what is make and model of your board ?

---

### Post by Ranjit on 2007-01-15
Hello Kyran,
I have same problem. 
Can you atleast get a text console?
If you do you can edit /etc/X11/xorg.conf
Point it to appropriate PCI Bus ID.
Then startx.

if you can go on internet
apt-get install nvidia-glx will do it for you.

There is no BIOS option on i810 for disabling onboard video but
PCI is first polled for video by default.
Ranjit.

---

### Post by Kyran on 2007-01-15
Motherboard: 82801AA
Inbuilt GPU: 82810E

I guess I could install the OS using the Alternate CD (unless it tries to detect which graphic card to use for the installion) log-in using safe-mode and try to install the drivers. Its not going to be easy blind-folded though.

Right now however my aim is the get the Live CD working so I can test the rest of my Gateway's hardware.

EDIT: Come to think of it that might work, since its the X Server that sets the graphic drivers and that. Still, I'll like to test it on the Live CD first so I can see if it will fit with this computers work load.

---

### Post by aberry5555 on 2007-01-15
well if you can get it to work on the i810 card (using "vesa" drivers if i810 drivers are not installed) you can go in to the gui and edit the xorg.conf from there. then you press ctrl-alt-backspace (not delete) which will log you off and restart the x server and it should, hopefully, go through to your secondary card.

---

### Post by Ranjit on 2007-01-16
I have following config: P-III 866MHz, i810E mobo, PCI GeForceFX5200.
Only method is to remove PCI graphic card. Attach monitor to i810 vga
port. Boot with Edgy Eft 6.10 CD. It starts OK. Do the install from GUI.
After reboot install nvidia drivers. Make changes to xorg.conf. Reboot.
Attach monitor to vga of graphic card. Restart and login to edgy. Try it.:-?

---

