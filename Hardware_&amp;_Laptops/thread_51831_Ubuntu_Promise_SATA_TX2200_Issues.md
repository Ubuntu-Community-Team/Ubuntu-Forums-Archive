---
title: "Ubuntu Promise SATA TX2200 Issues"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by Pumbaa on 2005-07-25
Hey everyone,

I'm not sure if this has been covered before but I've been scouring the 'Net trying to find help with getting my SATA drives to work under Ubuntu 5.04 and am having no luck what so ever. I'm using a Promise FastTrack TX2200 controller card and have two SATA drives connected to it (not in a RAID configuration). But for some reason Ubuntu will not see the drives at all, there is nothing within /dev/ which links to the drives (no sda/sr0 blocks). Initially the drives were set up in a RAID 0, I checked lsmod and found sata_promise module running, so I tried to use dmraid to find the RAID, but it kept saying "No Software RAID found". So I went into the BIOS, killed the RAID so now the drives are running as seperate individual drives, the sata_promise module is still running, but still no items available in /dev/ which will allow me to mount them.

Now within the System Configuration the Sata card is listed as a PCI card but the module section is listed as "Unknown". This leads me to believe that the OS is seeing the presence of the SATA Raid Controller, but is not linking a module with it. From what I've read the sata_promise module is the one that this card should be using, anyone know how I can link the sata_promise module to this device??
According to the Promise website, the card should be supported under linux as they have 2.4 kernel driveers, and I'm assuming with the presence of the sata_promise module, that the drivers are supported natively by the 2.6 kernel.

Is there anything else I can do to get my system to see the SATA drives?? It's 240GB of space I could really use and I honestly don't want to have to go back to Windows.

Any help would be greatly appreciated.

Thanks,

~Pumbaa

---

### Post by ioliver on 2005-07-26
The output of the relevant part of dmesg would help greatly. You should see the card being spotted, the ata ports being interrated, scsi devices being mapped to them and then finally devices of the type /dev/sd? being created.
Regards
Ian

---

