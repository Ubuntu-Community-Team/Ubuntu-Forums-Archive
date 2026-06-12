---
title: "SATA disk is not recognized, boot fails"
date: 2010-09-18
forum: Hardware
---

### Post by kelimi on 2010-09-18
HDD: Segate Barracude LP 500GB (ST3500412AS)
Motherboard chipset: nForce 630A MCP

I bought a brand new Segate Barracude LP 500GB (ST3500412AS), and if it   is attached to my server, it just won't boot. I tried it with my   currently installed Ubuntu 10.4 server, a 10.4 Desktop livecd and also   with the 10.4 Server installer disk (in recovery mode), kernel is   2.6.32-24-generic in all versions if I'm correct. The system always fails during   boot.

I tried using different SATA cables and onbord connectors, switching   AHCI/IDE, no matter what I do. As soon as I remove the disk, the system   can boot. By the way my mobo is an ASRock ALiveNF7G-GLAN.

I tired adding the disk to a different computer with Windows 7 and it was recognized correctly.

The errors I get periodically during boot until the 180 sec timeout:

```

[...] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[...] ata3.00: irq_stat 0x40000008
[...] ata3.00: failed command: READ FPDMA QUEUED
[...] ata3.00: cmd 60/08:00:28:60:38/00:00:3a:00:00/40 tag 0 ncq 4096 in
[...]          res 41/40:08:20:60:38/00:00:3a:00:00/00 Emask 0x409 (media error) <F>
[...] ata3.00: status: { DRDY ERR }
[...] ata3.00: error: { UNC }
[...] ata3.00: configure for UDMA/133
[...] ata3: EH complete

```In the end I get this timeout:

```
udevadm settle - timeout of 180 seconds reached, the event queue contains:   
/sys/devices/pci0000:00/0000:00:09.0/host2/taget2:0:0/2:0:0:0/block/sda (1045)
[...] Kernel panic - not syncing: Attempted to kill init!
```[http://wwww.ubuntuforums.org/showthread.php?t=1566664](http://wwww.ubuntuforums.org/showthread.php?t=1566664) describes a similar problem.

---

### Post by kelimi on 2010-09-18
I've tried the HDD out with a third computer with an MSI 760GM-E51 motherboard (chipset: AMD 760G).

With Windows 7, the disk was properly recognized and I could format is.
Then with Ubuntu 10.4 server install CD (recovery mode) I got the same errors as before...

---

### Post by kelimi on 2010-09-18
The disk was defective. Even it seemed to be working under Windows, Segate's hard drive tester showed several errors.

---

