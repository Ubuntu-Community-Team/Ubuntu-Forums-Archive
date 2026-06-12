---
title: "Travan ATAPI IDE Tape Drive is not recognized Kubuntu 9.10"
date: 2010-03-13
forum: Hardware
---

### Post by marvin81 on 2010-03-13
Dear all,

I have a big problem. My internal IDE Tape drive "Travan 40" from Quantum/Seagate is not recognized by Kubuntu 9.10. I have no idea why. The BIOS recognizes the tape drive and it works fine under Windows XP.

It seems to me that I have to load the module ide-scsi. But I just get an error message:

FATAL: Module ide_scsi not found.


My drive configuration is as follows: 



Attached devices: 



Host: scsi0 Channel: 00 Id: 00 Lun: 00 

Vendor: ATA Model: WDC WD3200AAKS-0 Rev: 01.0 Type: 

Direct-Access ANSI SCSI revision: 05 



Host: scsi2 Channel: 00 Id: 00 Lun: 00 

Vendor: HL-DT-ST Model: DVD-RW GWA-4160B Rev: A303 

Type: CD-ROM ANSI SCSI revision: 05 

Can someone help?
Thanks a lot! ;)

---

### Post by schmidtbag on 2010-08-16
any idea how to get this to work?  i've got the same issue

---

### Post by marvin81 on 2010-08-17
Now, I have a solution!

The problem was the hardware configuration: the tape drive was the only drive set as slave on the secondary IDE controller. In Windows this is not a problem - but under Ubuntu the drive is not recognized.

How to solve it: Connect your tape drive together with another drive on the same IDE controller. E.g. CD-ROM Drive as master, IDE-Tape as slave on the primary (or secondary) IDE-Controller. It should work then! :D

Yours,
Marvin81 :popcorn:

---

### Post by schmidtbag on 2010-08-17
hmmm... thats definitely not the issue for me.  i've already had it like that and i've used an ata to usb converter and it still gives me the same issues.

i tried the device in windows 7 and virtual windows xp and neither of them are capable of detecting a tape.  they know the drive exists but they don't see a tape.

in linux, the device is detected but when i try an mt command, nothing happens, it just sits there doing nothing but it doesn't go back to the command line

---

