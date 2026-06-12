---
title: "USB Creator does not see my USB drive"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by Craig73 on 2008-12-22
I have a 1GB lexar secure usb drive, that I plugged into an Inspiron 700M.  I can see, open and create files on the drive... but USB Creator does not see the drive.  Any ideas?  

I'm using Ubuntu 8.10 / USB Creator 0.1.10

(It was FAT32 formatted on Windows.  I did reformat the drive again to FAT32 just to see if that made a difference, it didn't, well other than annoy me that formatting disks in Ubuntu does not 'just work')

---

### Post by Craig73 on 2008-12-22
I see nothing in the logs that would suggest a problem with my drive.

MESSAGES ###############################################################

Dec 22 16:10:26 pluto kernel: [477837.025430] usb 1-1: USB disconnect, address 9
Dec 22 16:10:31 pluto kernel: [477841.985100] usb 1-1: new high speed USB device using ehci_hcd and address 10
Dec 22 16:10:31 pluto kernel: [477842.172983] usb 1-1: configuration #1 chosen from 1 choice
Dec 22 16:10:31 pluto kernel: [477842.211382] scsi6 : SCSI emulation for USB Mass Storage devices
Dec 22 16:10:36 pluto kernel: [477847.218753] scsi 6:0:0:0: Direct-Access     LEXAR    JUMPDRIVE SECURE 1000 PQ: 0 ANSI: 0 CCS
Dec 22 16:10:36 pluto kernel: [477847.238546] sd 6:0:0:0: [sdb] 2030592 512-byte hardware sectors (1040 MB)
Dec 22 16:10:36 pluto kernel: [477847.240431] sd 6:0:0:0: [sdb] Write Protect is off
Dec 22 16:10:36 pluto kernel: [477847.242789] sd 6:0:0:0: [sdb] 2030592 512-byte hardware sectors (1040 MB)
Dec 22 16:10:36 pluto kernel: [477847.244795] sd 6:0:0:0: [sdb] Write Protect is off
Dec 22 16:10:36 pluto kernel: [477847.246105]  sdb: sdb1
Dec 22 16:10:36 pluto kernel: [477847.293853] sd 6:0:0:0: [sdb] Attached SCSI disk
Dec 22 16:10:36 pluto kernel: [477847.294218] sd 6:0:0:0: Attached scsi generic sg2 type 0

SYSLOG ##################################################################
Dec 22 16:15:37 pluto chipcardd[4726]: devicemanager.c: 3373: Changes in hardware list
Dec 22 16:15:47 pluto kernel: [478157.888071] usb 1-1: new high speed USB device using ehci_hcd and address 11
Dec 22 16:15:47 pluto kernel: [478158.058961] usb 1-1: configuration #1 chosen from 1 choice
Dec 22 16:15:47 pluto kernel: [478158.103196] scsi7 : SCSI emulation for USB Mass Storage devices
Dec 22 16:15:47 pluto kernel: [478158.114297] usb-storage: device found at 11
Dec 22 16:15:47 pluto kernel: [478158.114314] usb-storage: waiting for device to settle before scanning
Dec 22 16:15:49 pluto chipcardd[4726]: devicemanager.c: 3373: Changes in hardware list
Dec 22 16:15:52 pluto kernel: [478163.112339] usb-storage: device scan complete
Dec 22 16:15:52 pluto kernel: [478163.114317] scsi 7:0:0:0: Direct-Access     LEXAR    JUMPDRIVE SECURE 1000 PQ: 0 ANSI: 0 CCS
Dec 22 16:15:52 pluto kernel: [478163.133514] sd 7:0:0:0: [sdb] 2030592 512-byte hardware sectors (1040 MB)
Dec 22 16:15:52 pluto kernel: [478163.135510] sd 7:0:0:0: [sdb] Write Protect is off
Dec 22 16:15:52 pluto kernel: [478163.135525] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
Dec 22 16:15:52 pluto kernel: [478163.135534] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Dec 22 16:15:52 pluto kernel: [478163.142521] sd 7:0:0:0: [sdb] 2030592 512-byte hardware sectors (1040 MB)
Dec 22 16:15:52 pluto kernel: [478163.144513] sd 7:0:0:0: [sdb] Write Protect is off
Dec 22 16:15:52 pluto kernel: [478163.144529] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
Dec 22 16:15:52 pluto kernel: [478163.144537] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Dec 22 16:15:52 pluto kernel: [478163.152872]  sdb: sdb1
Dec 22 16:15:52 pluto kernel: [478163.222501] sd 7:0:0:0: [sdb] Attached SCSI disk
Dec 22 16:15:52 pluto kernel: [478163.223402] sd 7:0:0:0: Attached scsi generic sg2 type 0

---

### Post by Craig73 on 2009-01-14
bump

---

### Post by Craig73 on 2009-01-23
bump

---

### Post by Craig73 on 2009-01-31
bump

---

