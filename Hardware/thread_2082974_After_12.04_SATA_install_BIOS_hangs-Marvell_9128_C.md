---
title: "After 12.04 SATA install BIOS hangs-Marvell 9128 Controller-Gigabyte X58A-UD5 Mothe"
date: 2012-11-11
forum: Hardware
---

### Post by MarkAtNeerim on 2012-11-11
This is a new Mythbuntu 12.04 Install.

I have a Gigabyte GA-X58A-UD5 Motherboard,  on this motherboard, SATA Ports 0 & 1 are connected to a Marvell SATA 3, 9128 controller,  the only drive in the system (for the install) is a WD1500ADFD connected to Port 0.

The system will boot from the install DVD, find the hard disk and do a full install.

The problem occurs when I reboot the system.  The BIOS can no longer find the hard disk and hangs on initialization.  

This has happened on 2 seperate installs using 2 different WD hard disks,  the other being a WD1500HLFS.

I can take the hard disk to a windows 7 system and hot plug to  SATA,  Windows finds the disk,  I then do a low level format to the disk and can repeat the install process on the Mythbuntu machine with the exact same result.

The only solution I have found is to not use Ports 0 & 1 on this motherboard.   Using the Intel or Gigabyte controller ports solves the problem even if I first install on the Marvell 9128 ports.

---

