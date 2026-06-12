---
title: "GRUB &amp; USB Keyboards"
date: 2009-01-15
forum: Hardware
---

### Post by monikersupreme on 2009-01-15
So I've finally got my dual boot XP + Ubuntu v8.10 installed last night, went to reboot my workstation, and low & behold when GRUB boots it seems to disable my USB keyboard (and thus preventing me from selecting my desired OS).

The behavior is as follows... when I reboot my workstation my keyboard will briefly activate such that if I want to enter the BIOS it is possible to do so, however the moment GRUB boots the keyboard is deactivated. 

At this point, GRUB usually times out and selects Ubuntu by default.

The specs of my workstation are as follows:

MSI K9MM-V / AM2 5200+ / 2GB DDR800
2 x 250GB SATA / BFG NVIDIA 7800GS AGP

(ignore the specs in my sig as they are for my laptop)

My workaround at present is to plug in a PS/2 keyboard and use this to select the OS from GRUB... however this is far from optimal.

Is there any way to prevent GRUB from deactivating my USB keyboard?

---

### Post by electrogeist on 2009-01-15
Take a look in the BIOS setup, for an option for legacy usb keyboard/mouse support.

---

### Post by monikersupreme on 2009-01-16
Is this for sure a BIOS issue?

The reason being that, the version of the MSI BIOS that I'm using seems to have a problem when any of the USB Emulation settings are activated... causing the workstation to lock up on boot (and granted this is an MSI issue and nothing to do with Ubuntu)... however it seems odd that following POST I have access to the keyboard (and thus can access the BIOS) but the moment GRUB boots I loose all USB connectivity...

If this is a BIOS issue then I am most likely hosed but I'd really like to keep my Ubuntu partition on my workstation as it's increasing coming in handy and seems to get better performance on my workstations (ageing) hardware.

Any possibility that I might be able to configure GRUB to not "turn off" USB connectivity on boot?

---

### Post by Yashiro on 2009-01-16
I don't think grub turns anything off is the point?
My USB kb works fine in bios,grub etc. (Asus A8N c.2005)

You need to fix your bios issue I think.

---

### Post by jespdj on 2009-01-16
Isn't there a newer version of the BIOS for your particular brand and model of motherboard available that might fix the problems you describe? Look on the website of the motherboard manufacturer if there is an update available.

---

