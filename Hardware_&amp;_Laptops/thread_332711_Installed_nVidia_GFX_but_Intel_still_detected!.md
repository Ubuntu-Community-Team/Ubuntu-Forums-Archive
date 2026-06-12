---
title: "Installed nVidia GFX but Intel still detected!"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by megamaced on 2007-01-06
MAJOR problem: I upgraded the Intel integrated graphics with a PCI nVidia Geforce FX 5200. Now the computer will not boot into X.

Things I have tried:

Disabling the integrated graphics in the BIOS
Typing 'sudo dpkg-reconfigure xserver-xorg

But the problem is it keeps detecting the Intel graphics. How can I force it to use the new nVidia card instead?

Any help would be very much welcome!

PS. I am running Kubuntu 6.06

---

### Post by Frogger on 2007-01-06
You need to manually tell X to look to the GFFX 5200.  You will have to edit your xorg.conf manually.

First, you need to find your PCI id of the GFFX 5200 so type:
lspci

Then find the GFFX 5200 from the list, it will be formatted like 00:00.00, write it down

load the Xconfig file (with root privleges):
sudo nano /etc/X11/xorg.conf

find the device section (it looks like this):
Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graph
ics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Change it to your card (something like this, not including the ()):
Section "Device"
        Identifier      "GFFX 5200 (this does not matter much)"
        Driver          "nv (the open source nvidia driver) "
        BusID           "PCI:0:0:0(change this to the pci id of your GFFX 5200)"
EndSection

Then tell X to look use the device in the screen section:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Change this to what you put in identifier"

then try:
startx

if that works reboot by opening an xterm and typing:
sudo reboot

Good Luck!

---

### Post by DarkN00b on 2007-01-06
Also, you may need to change your BIOS settings to disable onboard video.

---

### Post by megamaced on 2007-01-07
Thanks Frogger! Problem solved! :-D

---

### Post by megamaced on 2007-04-17
Is there anyway to tell the kernel at boot time to use the PCI graphics card? Although my current solution works fine once the distribution has been installed, I can't run LiveCDs. I must have a stupid BIOS because I've selected PCI as the default graphics output. Still every liveCD I want to use detects and configures the Intel integrated graphics. When this happens, it basically means the LiveCD never boots and just freezes

---

