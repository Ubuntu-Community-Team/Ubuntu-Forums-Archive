---
title: "CD/DVD burner only partially functioning"
date: 2008-04-22
forum: Hardware
---

### Post by potterpoole on 2008-04-22
have done something to my dvd burner. It wont play cd music but it reads data just fine I am including output from commands I found and ran in the shell. and my fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=ac387d57-50fe-4ffa-a698-344f61002fdd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=e48dcf72-226f-463e-9ac2-c02f7fcc54ea none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0




dean@dean-desktop:~$ mount /cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dean@dean-desktop:~$  dmesg | tail
[  693.364000] ide: failed opcode was: unknown
[  693.364000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[  693.364000] end_request: I/O error, dev hdc, sector 1024
[  693.364000] UDF-fs: No partition found (1)
[  693.392000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[  693.392000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[  693.392000] ide: failed opcode was: unknown
[  693.392000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[  693.392000] end_request: I/O error, dev hdc, sector 64
[  693.392000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
dean@dean-desktop:~$ 




dean@dean-desktop:~$ sudo grep -i dvd /var/log/dmesg
[sudo] password for dean:
[    7.992000] hdc: DVDRW IDE 16X, ATAPI CD/DVD-ROM drive
[    8.764000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache<4>hdc: drive side 80-wire cable detection failed, limiting max speed to UDMA33



dean@dean-desktop:~$ sudo grep -i cd /var/log/dmesg
[   22.264330] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   22.264579] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   22.264610] uhci_hcd 0000:00:10.0: irq 11, io base 0x0000d000
[   22.367363] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   22.367393] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   22.367423] uhci_hcd 0000:00:10.1: irq 3, io base 0x0000d400
[   22.471320] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   22.471352] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   22.471381] uhci_hcd 0000:00:10.2: irq 10, io base 0x0000d800
[   22.578838] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   22.579280] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   22.579342] ehci_hcd 0000:00:10.3: irq 5, io mem 0xdc000000
[   22.579350] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.604000] usb 4-5: new high speed USB device using ehci_hcd and address 2
[    7.992000] hdc: DVDRW IDE 16X, ATAPI CD/DVD-ROM drive
[    8.764000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache<4>hdc: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[    8.764000] Uniform CD-ROM driver Revision: 3.20


Thanks for any help I can get.

---

