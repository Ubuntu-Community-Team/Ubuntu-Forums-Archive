---
title: "Handspring Visor won't sync with JPilot"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by g4c9z on 2007-08-14
Hi,

I just re-installed Ubuntu, was formerly using Dapper Drake, now using 7.04 (Fiesty or something).  My Handspring Visor, which has a USB connection, was previously working, now it's not working so well.

At first it wouldn't sync at all, but then I realized I had to modprobe the visor module.  I don't know why I didn't have to do that in Dapper Drake.  That allowed the command-line tools like pilot-install-memo to correctly be able to install memos onto the PDA.

But when I try to sync it with JPilot, either with the jpilot-sync command or when opening JPilot and syncing it through the GUI, the following error message appears on the PDA immediately after the start of the sync:

"The connection between your handheld computer and the desktop was lost.  Some of your data was NOT backed up.  Please check your setup and try again."

I'm using udev (the default), which creates the device for the PDA when the hotsync button is pressed, according to the following rule in the file /etc/udev/rules.d/10-local.rules:

BUS=="usb", SYSFS{product}=="Handspring Visor", KERNEL=="ttyUSB1", NAME="pilot", SYMLINK="visor %k", MODE="0666"

This causes the device to be created as /dev/pilot.

One possibility that I suspect is that I have to load (with modprobe) some other kernel module, but I don't know which one(s), other than the visor module that I already load.  The Handspring Visor mini-HOWTO suggests visor, usb-uhci, and usb-ohci, but the latter two do not seem to exist when I try to modprobe them.  Perhaps they're old and no longer used.  I do have usbserial and usbcore loaded.

Some people on other threads say it seems to work to change the JPilot device to "usb:" instead of /dev/pilot.  This doesn't seem to have an effect for me.

Thanks for reading, and any hints would be appreciated.

---

### Post by g4c9z on 2007-08-18
From Googling around, I found someone who suggested that I change the Serial Rate of the connection to 115200 (you can do this in the JPilot preferences, I don't know about KPilot) and suddenly the problem was fixed.

I don't understand why that should fix it, though, because in the JPilot dialog it says that the Serial Rate does not affect USB. I think it's a bug, but I don't know if it's an Ubuntu bug or a J-Pilot bug.

---

