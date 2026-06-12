---
title: "DAT tape drive not found"
date: 2008-04-25
forum: Hardware
---

### Post by jtappin on 2008-04-25
On my system I have a (fairly elderly) DAT-3 drive, connected to a BusLogic SCSI controller.

On versions from Breezy up to Gutsy (32-Bit), it worked fine, however I have done a rebuild & upgrade to Hardy (64 bit) and now I don't get any tape devices.

According to the SCSI BIOS screen the drive is seen by the SCSI controller, and inserting a tape results in the usual sequence of winding -- so I don't think any connections have come adrift. 

lsmod and lspci both show that the BusLogic controller is being seen correctly, but the st module isn't loaded, and manually doing:
modprobe st
loads the module, but still no /dev/st? or /dev/nst? and /var/log/syslog contains the message:
Apr 25 17:57:58 xena kernel: [  569.442905] st: Version 20070203, fixed bufsize 32768, s/g segs 256
Apr 25 17:57:58 xena kernel: [  569.443104] Driver 'st' needs updating - please use bus_type methods


Does anyone have any clues what to try next?

I should add that both in the current and previous builds of the machine the DAT drive was/is the only thing connected to the controller.

---

