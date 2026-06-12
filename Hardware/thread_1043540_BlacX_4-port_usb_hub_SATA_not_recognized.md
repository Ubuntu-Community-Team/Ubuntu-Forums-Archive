---
title: "BlacX 4-port usb hub SATA not recognized"
date: 2009-01-18
forum: Hardware
---

### Post by mikeklein on 2009-01-18
I plugged in hub on already running machine. It w/appear from dmesg/etc. that a dumb usb device was plugged in...none of the hubs worked with my bt dongle, etc.

After a reboot the hub works and is recognized in dmesg as a 4-port hub...but I have no visibility to the docked SATA in it.

I've done fdisk -l and other cmds...but only my SCSI on mobo and an attached WD 1394 show up...no SATA.

Dmesg only appears to show 4-port hub being initialized...nothing about SATA, fstypes, etc.

Any ideas?

---

### Post by mikeklein on 2009-01-18
I can pull the hub's usb cable, wait a few sec, and plug back in and I see 4-port hub reregistered, my bt dongle on one port reactivates...all is great.

But zero sata/hd messages. I've read other non-hub forms of this sata dock work great.

---

