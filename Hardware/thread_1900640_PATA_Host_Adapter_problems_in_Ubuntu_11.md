---
title: "PATA Host Adapter problems in Ubuntu 11"
date: 2011-12-26
forum: Hardware
---

### Post by CaptNibor on 2011-12-26
Ubuntu recognizes the host adapter but nothing attached to it.  I have a DVD drive and a hard drive as well.  I can see it in Disk Utility.  Any suggestions on how to get Ubuntu to acknowledge the drives attached to the adapter?


Thanks

---

### Post by wolfen69 on 2011-12-26
Are master and slave set correctly?

---

### Post by CaptNibor on 2011-12-26
Yeah, I realized I didn't give enough details.

The host adapter is a two port IDE add-on card.  The two drives are set as master (I think) one on each port simply because the drives are too far apart to connect to one port with the drive cables I have.  Windows XP can access all drives (Dual boot system).  I figured if Windows can see the drives, Ubuntu would have no trouble unless I need a special driver for the card.  The card has this information on it:  MMUI-VT6410.  I don't know the brand but it has a VIA Technologies chip on it.  Ubuntu reads it as "VT6410 ATA 133 RAID controller"

Thanks.

---

### Post by AmUtkiek on 2011-12-31
I'm having more or less the same problem. I'm using a DawiControl DC-133 Card (latest firmware), an IDE controller on a PCI Slot as the mainboard doesn't have an onboard IDE controller. A hard disk (primary master) and a DVD drive (secondary master) are connected. When Ubuntu (Oneiric) is freshly started, the drives can be mounted and accessed but only for a short while. Drives on the onboard SATA controller are working fine. I tried variuos setups on the IDE controller but nothing seems to be stable... Any ideas?

---

