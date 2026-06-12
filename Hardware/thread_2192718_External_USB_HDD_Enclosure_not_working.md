---
title: "External USB HDD Enclosure not working"
date: 2013-12-09
forum: Hardware
---

### Post by steven0brock on 2013-12-09
I have a brand new Dynex HDD 3.5 enclosure with a 500GB WD drive inside.
Worked fine on a desktop box with win7.
Desktop box crashed.

Plugged the enclosure into my laptop running ubuntu 12.04 -- nothing happens.
Plugged in an old 2.5 enclosure -- works fine.

Any suggestions?

---

### Post by Bashing-om on 2013-12-09
steven0brock; Hello ,

Maybe, the device was not "safely removed" and has a lock on the file system ?
How about taking the drive to a Windows machine and there "unmounting " the drive and see what results .

[INDENT][INDENT]hey, it is a thought
[/INDENT][/INDENT]

---

### Post by steven0brock on 2013-12-09
Found the fix,

Must comment these lins out in 80-udisks.rules:

##############################################################################################################


# Check if a disk is ATA SMART capable
#


# USB ATA enclosures with a SAT layer
# KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="usb", ENV{DEVTYPE}=="disk", IMPORT{program}="udisks-probe-ata-smart $tempnode"


# ATA disks driven by libata
# KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="ata", ENV{DEVTYPE}=="disk", IMPORT{program}="udisks-probe-ata-smart $tempnode"


# ATA disks connected via SAS (not driven by libata)
# KERNEL=="sd*[!0-9]", ATTR{removable}=="0", ENV{ID_BUS}=="scsi", ENV{DEVTYPE}=="disk", ENV{ID_VENDOR}=="ATA", IMPORT{program}="udisks-probe-ata-smart $tempnode"

---

