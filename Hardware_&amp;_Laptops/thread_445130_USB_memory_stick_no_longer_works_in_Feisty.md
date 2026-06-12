---
title: "USB memory stick no longer works in Feisty"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by willsomebody on 2007-05-15
I have never had any problem with Ubuntu before.  I used 6.06 and 6.10 for a year total and never had trouble with USB memory.  Now that I have upgraded to Feisty, I have had much trouble with it.  I have tried 4 different USB memory sticks including one SD card that flips out a USB port.  I can sometimes get one to work for 15 minutes max by restarting my computer and taking it in and out of the USB port, but most of the time it just ignores the device.  I have tried all of the ports on my computer with no better luck, also I have no problems with my iPod in Banshee or my USB printer and scanner combo.  Does anyone know what is causing this problem and/or how to fix it?  If I must, I can continue plugging it into my windows computer and accessing it over my network, but that defeats the convenience of the USB memory. :confused:


I have an Asus a7n8x mobo with a Duron 1.8 Ghz and an Nvidia GeForce fx 5500 with 128 mb of dedicated graphics ram and a single 512 mb ram chip on my motherboard.   I have tried SanDisk, Newegg, and RiDATA usb drives to no avail, I recently tried Gparted and Storage Device Manager, but neither detected it.  All of my USB memory sticks have worked on other computers.

---

### Post by Kobalt on 2007-05-15
What are your hardware specs : motherboard type, laptop model (if it's one), etc. ?

---

### Post by willsomebody on 2007-05-15
Per your request, I added the specs of my desktop. feel free to ask me for any more information that is necessary

---

### Post by willsomebody on 2007-05-15
I have solved my problem with 'gksu modprobe -r ehci_hcd'.  I only have to do it once and my problem is solved.  I hope this helps some other people with this same problem

---

### Post by mh114 on 2007-05-16
> **willsomebody said:**
> I have solved my problem with 'gksu modprobe -r ehci_hcd'.  I only have to do it once and my problem is solved.  I hope this helps some other people with this same problem
This worked for me too, thanks! :) What's strange that I did try that before, but it just hanged. I did sudo though, in terminal, but that shouldn't make any difference.. Anyway, glad to see my USB disk working again, hopefully it stays working after restart as well.

EDIT: Didn't work after restart, but can be fixed with the same command. :)

---

