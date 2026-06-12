---
title: "mdadm raid mirror problems"
date: 2011-10-10
forum: Hardware
---

### Post by kevpatts on 2011-10-10
Hey all,

My mdadm RAID mirrors are temporarily stalling every time I boot, causing the boot to take 30 seconds longer than it should. There seems to be no other problems with the arrays and I haven't lost any data.

I can't find any relevant bugs or similar issues to this reported. Is anyone else having this problem?

This (~approx) logging is recorded every time I boot in kern.log:
```
Oct  3 16:40:15 localhost kernel: [    1.719284] usbhid: USB HID core driver
Oct  3 16:40:15 localhost kernel: [    1.736412]  md1: unknown partition table
Oct  3 16:40:15 localhost kernel: [    1.738060] md: bind<sdb1>
Oct  3 16:40:15 localhost kernel: [    1.740163] md/raid1:md0: active with 2 out of 2 mirrors
Oct  3 16:40:15 localhost kernel: [    1.740184] md0: detected capacity change from 0 to 15998050304
Oct  3 16:40:15 localhost kernel: [    1.754871]  md0: unknown partition table
Oct  3 16:40:15 localhost kernel: [    1.861306] EXT4-fs (md1): INFO: recovery required on readonly filesystem
Oct  3 16:40:15 localhost kernel: [    1.861311] EXT4-fs (md1): write access will be enabled during recovery
Oct  3 16:40:15 localhost kernel: [    2.048021] usb 4-1: new low speed USB device number 2 using ohci_hcd
Oct  3 16:40:15 localhost kernel: [    2.146103] ata3.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x400000 action 0x6 frozen
Oct  3 16:40:15 localhost kernel: [    2.146117] ata3.00: irq_stat 0x08000000, interface fatal error
Oct  3 16:40:15 localhost kernel: [    2.146120] ata3: SError: { Handshk }
Oct  3 16:40:15 localhost kernel: [    2.146124] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146129] ata3.00: cmd 61/08:00:c0:f1:5c/00:00:3b:00:00/40 tag 0 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146131]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146133] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146135] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146140] ata3.00: cmd 61/10:08:60:f2:5c/00:00:3b:00:00/40 tag 1 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    2.146141]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146143] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146145] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146149] ata3.00: cmd 61/08:10:90:f2:5c/00:00:3b:00:00/40 tag 2 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146150]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146152] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146154] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146158] ata3.00: cmd 61/08:18:a8:f2:5c/00:00:3b:00:00/40 tag 3 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146159]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146161] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146163] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146167] ata3.00: cmd 61/10:20:00:f3:5c/00:00:3b:00:00/40 tag 4 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    2.146174]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146176] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146178] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146182] ata3.00: cmd 61/10:28:18:f3:5c/00:00:3b:00:00/40 tag 5 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    2.146183]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146185] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146187] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146191] ata3.00: cmd 61/08:30:48:f3:5c/00:00:3b:00:00/40 tag 6 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146192]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146194] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146195] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146200] ata3.00: cmd 61/08:38:58:f3:5c/00:00:3b:00:00/40 tag 7 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146201]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146203] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146204] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146209] ata3.00: cmd 61/60:40:d0:e1:5c/00:00:3b:00:00/40 tag 8 ncq 49152 out
Oct  3 16:40:15 localhost kernel: [    2.146209]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146212] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146213] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146217] ata3.00: cmd 61/18:48:48:e2:5c/00:00:3b:00:00/40 tag 9 ncq 12288 out
Oct  3 16:40:15 localhost kernel: [    2.146218]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146220] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146222] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146226] ata3.00: cmd 61/08:50:90:e2:5c/00:00:3b:00:00/40 tag 10 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146227]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146230] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146231] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146235] ata3.00: cmd 61/10:58:a0:e2:5c/00:00:3b:00:00/40 tag 11 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    2.146236]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146239] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146240] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146244] ata3.00: cmd 61/20:60:c8:e2:5c/00:00:3b:00:00/40 tag 12 ncq 16384 out
Oct  3 16:40:15 localhost kernel: [    2.146245]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146248] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146249] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146253] ata3.00: cmd 61/08:68:20:e3:5c/00:00:3b:00:00/40 tag 13 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146254]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146256] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146258] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146262] ata3.00: cmd 61/10:70:30:e3:5c/00:00:3b:00:00/40 tag 14 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    2.146263]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146265] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146267] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146282] ata3.00: cmd 61/08:78:30:e4:5c/00:00:3b:00:00/40 tag 15 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146283]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146285] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146289] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146293] ata3.00: cmd 61/08:80:d0:e4:5c/00:00:3b:00:00/40 tag 16 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146294]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146296] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146298] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146302] ata3.00: cmd 61/08:88:40:e6:5c/00:00:3b:00:00/40 tag 17 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146303]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146305] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146307] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146311] ata3.00: cmd 61/08:90:20:e7:5c/00:00:3b:00:00/40 tag 18 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146312]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146320] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146322] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146326] ata3.00: cmd 61/08:98:b8:e7:5c/00:00:3b:00:00/40 tag 19 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146327]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146329] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146331] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146335] ata3.00: cmd 61/08:a0:48:e8:5c/00:00:3b:00:00/40 tag 20 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146336]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146338] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146340] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146344] ata3.00: cmd 61/08:a8:08:e9:5c/00:00:3b:00:00/40 tag 21 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146345]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146347] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146349] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146353] ata3.00: cmd 61/08:b0:00:eb:5c/00:00:3b:00:00/40 tag 22 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146354]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146356] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146358] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146362] ata3.00: cmd 61/08:b8:90:eb:5c/00:00:3b:00:00/40 tag 23 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146363]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146365] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146367] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146371] ata3.00: cmd 61/08:c0:f0:ec:5c/00:00:3b:00:00/40 tag 24 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146372]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146374] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146376] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146380] ata3.00: cmd 61/08:c8:08:ed:5c/00:00:3b:00:00/40 tag 25 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146381]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146383] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146385] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146389] ata3.00: cmd 61/08:d0:60:ef:5c/00:00:3b:00:00/40 tag 26 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146390]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146392] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146394] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146398] ata3.00: cmd 61/08:d8:28:f0:5c/00:00:3b:00:00/40 tag 27 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146399]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146401] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146403] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146407] ata3.00: cmd 61/08:e0:e8:f0:5c/00:00:3b:00:00/40 tag 28 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146408]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146410] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146412] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146416] ata3.00: cmd 61/08:e8:00:f1:5c/00:00:3b:00:00/40 tag 29 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    2.146417]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146419] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146421] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    2.146425] ata3.00: cmd 61/10:f0:50:f1:5c/00:00:3b:00:00/40 tag 30 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    2.146426]          res 40/00:3c:58:f3:5c/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    2.146428] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    2.146432] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [    2.277243] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input4
Oct  3 16:40:15 localhost kernel: [    2.277337] generic-usb 0003:046D:C521.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:04.0-1/input0
Oct  3 16:40:15 localhost kernel: [    2.290134] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1/input/input5
Oct  3 16:40:15 localhost kernel: [    2.290256] generic-usb 0003:046D:C521.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:04.0-1/input1
Oct  3 16:40:15 localhost kernel: [    2.464022] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  3 16:40:15 localhost kernel: [    7.464027] ata3.00: qc timeout (cmd 0xec)
Oct  3 16:40:15 localhost kernel: [    7.464035] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Oct  3 16:40:15 localhost kernel: [    7.464038] ata3.00: revalidation failed (errno=-5)
Oct  3 16:40:15 localhost kernel: [    7.464044] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [    7.784020] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  3 16:40:15 localhost kernel: [    7.795271] ata3.00: configured for UDMA/133
Oct  3 16:40:15 localhost kernel: [    7.795309] ata3: EH complete
Oct  3 16:40:15 localhost kernel: [    7.797733] ata3.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x400000 action 0x6 frozen
Oct  3 16:40:15 localhost kernel: [    7.797736] ata3.00: irq_stat 0x08000000, interface fatal error
Oct  3 16:40:15 localhost kernel: [    7.797739] ata3: SError: { Handshk }
Oct  3 16:40:15 localhost kernel: [    7.797743] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797748] ata3.00: cmd 61/08:00:60:f6:5c/00:00:3b:00:00/40 tag 0 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797749]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797752] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797754] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797759] ata3.00: cmd 61/10:08:00:e0:dc/00:00:01:00:00/40 tag 1 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.797762]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797764] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797766] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797771] ata3.00: cmd 61/08:10:30:e0:dc/00:00:01:00:00/40 tag 2 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797772]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797774] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797776] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797780] ata3.00: cmd 61/10:18:40:e0:dc/00:00:01:00:00/40 tag 3 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.797782]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797784] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797786] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797790] ata3.00: cmd 61/08:20:78:e0:dc/00:00:01:00:00/40 tag 4 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797792]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797794] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797796] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797800] ata3.00: cmd 61/08:28:88:e0:dc/00:00:01:00:00/40 tag 5 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797801]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797804] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797806] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797810] ata3.00: cmd 61/28:30:e8:e0:dc/00:00:01:00:00/40 tag 6 ncq 20480 out
Oct  3 16:40:15 localhost kernel: [    7.797811]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797814] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797816] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797820] ata3.00: cmd 61/08:38:18:e1:dc/00:00:01:00:00/40 tag 7 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797821]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797824] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797826] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797830] ata3.00: cmd 61/08:40:28:e1:dc/00:00:01:00:00/40 tag 8 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797831]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797833] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797835] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797840] ata3.00: cmd 61/08:48:78:e1:dc/00:00:01:00:00/40 tag 9 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797841]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797843] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797845] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797850] ata3.00: cmd 61/08:50:10:00:dd/00:00:01:00:00/40 tag 10 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797851]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797853] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797855] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797860] ata3.00: cmd 61/08:58:20:00:dd/00:00:01:00:00/40 tag 11 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797861]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797863] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797868] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797873] ata3.00: cmd 61/08:60:68:e1:dc/00:00:06:00:00/40 tag 12 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797874]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797876] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797878] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797882] ata3.00: cmd 61/08:68:08:e0:5c/00:00:0c:00:00/40 tag 13 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797884]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797886] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797888] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797892] ata3.00: cmd 61/08:70:80:e0:5c/00:00:0c:00:00/40 tag 14 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797894]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797896] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797898] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797902] ata3.00: cmd 61/28:78:00:e1:5c/00:00:0c:00:00/40 tag 15 ncq 20480 out
Oct  3 16:40:15 localhost kernel: [    7.797904]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797906] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797908] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797912] ata3.00: cmd 61/10:80:08:e1:5d/00:00:0c:00:00/40 tag 16 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.797913]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797916] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797918] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797922] ata3.00: cmd 61/08:88:08:e0:dc/00:00:10:00:00/40 tag 17 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797923]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797926] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797928] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797932] ata3.00: cmd 61/08:90:80:e0:dc/00:00:10:00:00/40 tag 18 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797933]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797936] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797937] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797942] ata3.00: cmd 61/10:98:00:e1:dc/00:00:10:00:00/40 tag 19 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.797943]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797945] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797947] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797952] ata3.00: cmd 61/10:a0:30:e1:dc/00:00:10:00:00/40 tag 20 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.797953]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797955] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797957] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797961] ata3.00: cmd 61/10:a8:78:e1:dc/00:00:10:00:00/40 tag 21 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.797963]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797965] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797967] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797971] ata3.00: cmd 61/60:b0:d0:e1:5c/00:00:3b:00:00/40 tag 22 ncq 49152 out
Oct  3 16:40:15 localhost kernel: [    7.797973]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797975] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797977] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797981] ata3.00: cmd 61/08:b8:58:f3:5c/00:00:3b:00:00/40 tag 23 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797983]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797985] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797987] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.797991] ata3.00: cmd 61/08:c0:48:f3:5c/00:00:3b:00:00/40 tag 24 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.797992]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.797995] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.797997] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.798001] ata3.00: cmd 61/10:c8:18:f3:5c/00:00:3b:00:00/40 tag 25 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.798002]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.798005] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.798006] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.798016] ata3.00: cmd 61/10:d0:00:f3:5c/00:00:3b:00:00/40 tag 26 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.798018]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.798020] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.798022] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.798026] ata3.00: cmd 61/08:d8:a8:f2:5c/00:00:3b:00:00/40 tag 27 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.798028]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.798030] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.798032] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.798036] ata3.00: cmd 61/08:e0:90:f2:5c/00:00:3b:00:00/40 tag 28 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.798037]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.798040] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.798042] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.798046] ata3.00: cmd 61/10:e8:60:f2:5c/00:00:3b:00:00/40 tag 29 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [    7.798047]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.798050] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.798051] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [    7.798056] ata3.00: cmd 61/08:f0:c0:f1:5c/00:00:3b:00:00/40 tag 30 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [    7.798057]          res 40/00:ac:78:e1:dc/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [    7.798059] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [    7.798062] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [    8.116018] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  3 16:40:15 localhost kernel: [   13.116015] ata3.00: qc timeout (cmd 0xec)
Oct  3 16:40:15 localhost kernel: [   13.116018] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Oct  3 16:40:15 localhost kernel: [   13.116020] ata3.00: revalidation failed (errno=-5)
Oct  3 16:40:15 localhost kernel: [   13.116023] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [   13.436008] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  3 16:40:15 localhost kernel: [   13.447256] ata3.00: configured for UDMA/133
Oct  3 16:40:15 localhost kernel: [   13.447274] ata3: EH complete
Oct  3 16:40:15 localhost kernel: [   13.448539] ata3.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x400000 action 0x6 frozen
Oct  3 16:40:15 localhost kernel: [   13.448544] ata3.00: irq_stat 0x08000000, interface fatal error
Oct  3 16:40:15 localhost kernel: [   13.448547] ata3: SError: { Handshk }
Oct  3 16:40:15 localhost kernel: [   13.448549] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448553] ata3.00: cmd 61/08:00:b0:e1:dc/00:00:10:00:00/40 tag 0 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448555]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448557] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448559] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448563] ata3.00: cmd 61/08:08:f0:e1:dc/00:00:10:00:00/40 tag 1 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448567]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448569] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448571] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448576] ata3.00: cmd 61/10:10:20:e2:dc/00:00:10:00:00/40 tag 2 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448577]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448579] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448581] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448586] ata3.00: cmd 61/08:18:38:e2:dc/00:00:10:00:00/40 tag 3 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448587]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448589] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448591] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448595] ata3.00: cmd 61/10:20:50:e2:dc/00:00:10:00:00/40 tag 4 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448597]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448599] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448601] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448605] ata3.00: cmd 61/08:28:70:e2:dc/00:00:10:00:00/40 tag 5 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448607]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448609] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448611] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448615] ata3.00: cmd 61/08:30:78:e3:dc/00:00:10:00:00/40 tag 6 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448616]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448619] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448621] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448630] ata3.00: cmd 61/08:38:18:e4:dc/00:00:10:00:00/40 tag 7 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448631]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448634] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448636] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448640] ata3.00: cmd 61/08:40:b8:e8:dc/00:00:10:00:00/40 tag 8 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448641]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448644] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448646] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448650] ata3.00: cmd 61/08:48:d0:e7:dd/00:00:10:00:00/40 tag 9 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448651]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448654] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448655] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448660] ata3.00: cmd 61/10:50:30:e1:dc/00:00:10:00:00/40 tag 10 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448661]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448663] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448665] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448670] ata3.00: cmd 61/10:58:00:e1:dc/00:00:10:00:00/40 tag 11 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448671]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448673] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448675] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448680] ata3.00: cmd 61/08:60:80:e0:dc/00:00:10:00:00/40 tag 12 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448681]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448683] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448685] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448689] ata3.00: cmd 61/08:68:08:e0:dc/00:00:10:00:00/40 tag 13 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448691]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448693] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448695] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448699] ata3.00: cmd 61/10:70:08:e1:5d/00:00:0c:00:00/40 tag 14 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448701]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448703] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448705] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448709] ata3.00: cmd 61/28:78:00:e1:5c/00:00:0c:00:00/40 tag 15 ncq 20480 out
Oct  3 16:40:15 localhost kernel: [   13.448711]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448713] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448715] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448719] ata3.00: cmd 61/08:80:80:e0:5c/00:00:0c:00:00/40 tag 16 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448720]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448723] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448725] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448729] ata3.00: cmd 61/08:88:08:e0:5c/00:00:0c:00:00/40 tag 17 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448730]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448733] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448735] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448739] ata3.00: cmd 61/08:90:68:e1:dc/00:00:06:00:00/40 tag 18 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448740]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448743] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448744] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448749] ata3.00: cmd 61/08:98:20:00:dd/00:00:01:00:00/40 tag 19 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448750]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448752] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448754] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448759] ata3.00: cmd 61/08:a0:10:00:dd/00:00:01:00:00/40 tag 20 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448760]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448762] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448764] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448769] ata3.00: cmd 61/08:a8:78:e1:dc/00:00:01:00:00/40 tag 21 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448775]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448777] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448779] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448784] ata3.00: cmd 61/08:b0:28:e1:dc/00:00:01:00:00/40 tag 22 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448785]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448787] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448789] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448794] ata3.00: cmd 61/08:b8:18:e1:dc/00:00:01:00:00/40 tag 23 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448795]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448797] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448799] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448803] ata3.00: cmd 61/28:c0:e8:e0:dc/00:00:01:00:00/40 tag 24 ncq 20480 out
Oct  3 16:40:15 localhost kernel: [   13.448807]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448809] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448811] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448816] ata3.00: cmd 61/08:c8:88:e0:dc/00:00:01:00:00/40 tag 25 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448817]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448819] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448821] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448826] ata3.00: cmd 61/08:d0:78:e0:dc/00:00:01:00:00/40 tag 26 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448829]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448832] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448834] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448838] ata3.00: cmd 61/10:d8:40:e0:dc/00:00:01:00:00/40 tag 27 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448839]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448842] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448844] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448848] ata3.00: cmd 61/08:e0:30:e0:dc/00:00:01:00:00/40 tag 28 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448849]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448852] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448853] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448858] ata3.00: cmd 61/10:e8:00:e0:dc/00:00:01:00:00/40 tag 29 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   13.448859]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448861] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448863] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   13.448868] ata3.00: cmd 61/08:f0:60:f6:5c/00:00:3b:00:00/40 tag 30 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   13.448869]          res 40/00:4c:d0:e7:dd/00:00:10:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   13.448871] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   13.448874] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [   13.768008] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  3 16:40:15 localhost kernel: [   18.768020] ata3.00: qc timeout (cmd 0xec)
Oct  3 16:40:15 localhost kernel: [   18.768023] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Oct  3 16:40:15 localhost kernel: [   18.768025] ata3.00: revalidation failed (errno=-5)
Oct  3 16:40:15 localhost kernel: [   18.768028] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [   19.088019] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  3 16:40:15 localhost kernel: [   19.099254] ata3.00: configured for UDMA/133
Oct  3 16:40:15 localhost kernel: [   19.099271] ata3: EH complete
Oct  3 16:40:15 localhost kernel: [   19.103052] ata3: limiting SATA link speed to 1.5 Gbps
Oct  3 16:40:15 localhost kernel: [   19.103056] ata3.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x400000 action 0x6 frozen
Oct  3 16:40:15 localhost kernel: [   19.103058] ata3.00: irq_stat 0x08000000, interface fatal error
Oct  3 16:40:15 localhost kernel: [   19.103060] ata3: SError: { Handshk }
Oct  3 16:40:15 localhost kernel: [   19.103062] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103067] ata3.00: cmd 61/10:00:30:e9:dd/00:00:10:00:00/40 tag 0 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   19.103068]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103071] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103073] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103077] ata3.00: cmd 61/08:08:78:e0:dc/00:00:11:00:00/40 tag 1 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103079]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103081] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103089] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103094] ata3.00: cmd 61/08:10:00:e0:1c/00:00:12:00:00/40 tag 2 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103095]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103098] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103100] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103104] ata3.00: cmd 61/08:18:08:08:7d/00:00:1e:00:00/40 tag 3 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103105]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103108] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103110] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103114] ata3.00: cmd 61/10:20:00:e0:9c/00:00:1e:00:00/40 tag 4 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   19.103116]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103118] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103120] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103124] ata3.00: cmd 61/08:28:40:e0:9c/00:00:1e:00:00/40 tag 5 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103126]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103128] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103130] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103134] ata3.00: cmd 61/08:30:80:e0:9c/00:00:1e:00:00/40 tag 6 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103136]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103138] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103140] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103145] ata3.00: cmd 61/18:38:00:e1:9c/00:00:1e:00:00/40 tag 7 ncq 12288 out
Oct  3 16:40:15 localhost kernel: [   19.103146]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103149] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103150] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103155] ata3.00: cmd 61/18:40:20:e1:9d/00:00:1e:00:00/40 tag 8 ncq 12288 out
Oct  3 16:40:15 localhost kernel: [   19.103156]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103159] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103161] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103165] ata3.00: cmd 61/10:48:e0:ec:9d/00:00:1e:00:00/40 tag 9 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   19.103166]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103169] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103171] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103175] ata3.00: cmd 61/08:50:c0:ef:9d/00:00:1e:00:00/40 tag 10 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103177]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103179] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103181] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103185] ata3.00: cmd 61/08:58:d8:ef:9d/00:00:1e:00:00/40 tag 11 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103187]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103189] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103191] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103196] ata3.00: cmd 61/10:60:68:f0:9d/00:00:1e:00:00/40 tag 12 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   19.103197]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103199] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103201] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103206] ata3.00: cmd 61/08:68:80:e0:1c/00:00:22:00:00/40 tag 13 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103207]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103210] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103211] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103216] ata3.00: cmd 61/08:70:00:e1:1c/00:00:22:00:00/40 tag 14 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103217]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103220] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103222] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103226] ata3.00: cmd 61/10:78:58:e1:1c/00:00:22:00:00/40 tag 15 ncq 8192 out
Oct  3 16:40:15 localhost kernel: [   19.103227]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103230] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103232] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103238] ata3.00: cmd 61/08:80:10:e1:1d/00:00:22:00:00/40 tag 16 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103239]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103242] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103244] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103248] ata3.00: cmd 61/08:88:00:e1:5d/00:00:3b:00:00/40 tag 17 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103250]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103252] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103254] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103258] ata3.00: cmd 61/08:90:88:e1:5d/00:00:3b:00:00/40 tag 18 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103260]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103262] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103264] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103269] ata3.00: cmd 61/08:98:98:e1:5d/00:00:3b:00:00/40 tag 19 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103270]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103272] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103274] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103279] ata3.00: cmd 61/08:a0:e8:e1:5d/00:00:3b:00:00/40 tag 20 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103280]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103283] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103285] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103289] ata3.00: cmd 61/08:a8:58:e4:5d/00:00:3b:00:00/40 tag 21 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103290]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103293] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103295] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103299] ata3.00: cmd 61/08:b0:a0:e5:5d/00:00:3b:00:00/40 tag 22 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103303]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103305] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103307] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103312] ata3.00: cmd 61/08:b8:68:e7:5d/00:00:3b:00:00/40 tag 23 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103313]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103316] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103318] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103322] ata3.00: cmd 61/08:c0:80:e7:5d/00:00:3b:00:00/40 tag 24 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103323]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103326] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103328] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103332] ata3.00: cmd 61/08:c8:78:ed:5d/00:00:3b:00:00/40 tag 25 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103333]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103336] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103338] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103342] ata3.00: cmd 61/18:d0:08:ee:5d/00:00:3b:00:00/40 tag 26 ncq 12288 out
Oct  3 16:40:15 localhost kernel: [   19.103344]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103346] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103348] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103353] ata3.00: cmd 61/18:d8:40:ee:5d/00:00:3b:00:00/40 tag 27 ncq 12288 out
Oct  3 16:40:15 localhost kernel: [   19.103354]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103356] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103358] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103363] ata3.00: cmd 61/08:e0:70:ee:5d/00:00:3b:00:00/40 tag 28 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103364]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103367] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103368] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103373] ata3.00: cmd 61/08:e8:f0:e1:dc/00:00:10:00:00/40 tag 29 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103374]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103377] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103379] ata3.00: failed command: WRITE FPDMA QUEUED
Oct  3 16:40:15 localhost kernel: [   19.103383] ata3.00: cmd 61/08:f0:b0:e1:dc/00:00:10:00:00/40 tag 30 ncq 4096 out
Oct  3 16:40:15 localhost kernel: [   19.103390]          res 40/00:e4:70:ee:5d/00:00:3b:00:00/40 Emask 0x10 (ATA bus error)
Oct  3 16:40:15 localhost kernel: [   19.103392] ata3.00: status: { DRDY }
Oct  3 16:40:15 localhost kernel: [   19.103394] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [   19.420017] ata3: SATA link up <unknown> (SStatus 103 SControl 310)
Oct  3 16:40:15 localhost kernel: [   24.420019] ata3.00: qc timeout (cmd 0xec)
Oct  3 16:40:15 localhost kernel: [   24.420022] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Oct  3 16:40:15 localhost kernel: [   24.420024] ata3.00: revalidation failed (errno=-5)
Oct  3 16:40:15 localhost kernel: [   24.420027] ata3: hard resetting link
Oct  3 16:40:15 localhost kernel: [   24.740008] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct  3 16:40:15 localhost kernel: [   24.751259] ata3.00: configured for UDMA/133
Oct  3 16:40:15 localhost kernel: [   24.751277] ata3: EH complete
Oct  3 16:40:15 localhost kernel: [   24.861744] EXT4-fs (md1): recovery complete
Oct  3 16:40:15 localhost kernel: [   24.862088] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)
Oct  3 16:40:15 localhost kernel: [   38.439017] Adding 15623092k swap on /dev/md0.  Priority:-1 extents:1 across:15623092k 
Oct  3 16:40:15 localhost kernel: [   38.778977] EXT4-fs (md1): re-mounted. Opts: errors=remount-ro,user_xattr
```

Kevpatts

---

