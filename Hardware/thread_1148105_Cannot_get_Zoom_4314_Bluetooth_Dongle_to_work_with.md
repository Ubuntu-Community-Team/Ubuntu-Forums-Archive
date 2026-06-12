---
title: "Cannot get Zoom 4314 Bluetooth Dongle to work with Jaunty"
date: 2009-05-04
forum: Hardware
---

### Post by Tabun1970 on 2009-05-04
I recently purchased a Zoom Model 4314 USB Bluetooth Dongle to use on my Sony VAIO FW245 laptop. It came with a driver CD for Vista, which installed without issues and recognized the dongle and allowed me to pair and transfer files between my Samsung r450 Messenger phone. 

When I boot into Jaunty however, I cannot get any connectivity. When I run lsusb, I can see this particular line:
Bus 006 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

hcitool scan yields:

Device is not available: No such device

I installed obexftp and obexpushd and running obexftp -b ields:

Scanning ...
Inquiry failed.: No such device

The green flashing light on the dongle does not flash as it does in the windows setup, however, as I'm trying to rid myself of everything Windows, that does me no good.  I have seen the dongle light flashing once in an Ubuntu session, but have no idea how I did that. 

I'm trying to transfer files from my phone via bluetooth and also use a program called BlueProximity, which uses your phone or PDA as a locking mechanism based on proximity to laptop. I.E. when phone leaves vicinity of laptop, laptop screen locks and when phone returns to set distance, laptop unlocks.

Any help would be greatly appreciated for this Linux n00b!

---

### Post by Tabun1970 on 2009-05-04
Well...I found software called Blueman, installed it and all of my bluetooth problems are gone!

---

### Post by Tabun1970 on 2009-05-04
Well...Now that I've re-booted, the dongle is no longer recognized and I'm back to square one!

---

