---
title: "Thermaltake Silver River DUO External HDD Enclosure"
date: 2008-07-11
forum: Hardware
---

### Post by dburnett77 on 2008-07-11
I can't seem to get an ext. hd to recognize via USB.  It shows in Nautilus, but I can't mount it, or access it.

Here's some commands I've run, and their corresponding output:

root@david-desktop:/home/david# mount -t ext3 /dev/sdb /media/usb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@david-desktop:/home/david# dmesg | tail
[  134.586180] scsi2 : SCSI emulation for USB Mass Storage devices
[  134.586407] usb-storage: device found at 3
[  134.586413] usb-storage: waiting for device to settle before scanning
[  134.586421] usbcore: registered new interface driver usb-storage
[  134.586428] USB Mass Storage support registered.
[  139.575104] usb-storage: device scan complete
[  139.575952] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  139.582914] sd 2:0:0:0: [sdb] Attached SCSI disk
[  139.582976] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  150.267939] EXT3-fs: unable to read superblock


root@david-desktop:/home/david# mount -t autofs /dev/sdb /media/usb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


root@david-desktop:/home/david# dmesg | tail
[  134.586407] usb-storage: device found at 3
[  134.586413] usb-storage: waiting for device to settle before scanning
[  134.586421] usbcore: registered new interface driver usb-storage
[  134.586428] USB Mass Storage support registered.
[  139.575104] usb-storage: device scan complete
[  139.575952] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  139.582914] sd 2:0:0:0: [sdb] Attached SCSI disk
[  139.582976] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  150.267939] EXT3-fs: unable to read superblock
[  188.162112] autofs: called with bogus options


root@david-desktop:/home/david# lsusb
Bus 005 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  



Help would be appreciated.  Regards...

---

### Post by dburnett77 on 2008-07-11
Solved it myself.

Seems it wasn't documented that one of the connectors must be removed from the back panel.  Either the SATA or IDE cable.  Did that and now I can access the external unit.

Next question, can you get it to automount; that is, without having to issue the command:

mount -t ext2 /dev/sdb1 /mnt/sdb1

Thanks!

---

