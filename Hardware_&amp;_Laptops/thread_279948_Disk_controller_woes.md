---
title: "Disk controller woes"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by shiver on 2006-10-18
I recently upgraded to a system with an Asus P5W DH Deluxe mobo (I975X chipset), Core 2 Duo E6600 and MSI Geforce 7900 GTO. I'm using a Seagate SATA drive plugged into the first Intel ICH7 SATA controller, two IDE DVD drives in the Intel IDE controller and two old IDE HDDs in the JMicron IDE controller. 

When I installed Dapper, the installer showed a weird sdb drive that doesn't exist with some few hundred kB of space. It didn't cause problems -- yet -- so I didn't worry about it. 
It shows some messages in dmesg as well:

```

[   49.431780] ata2: dev 0 cfg 00:0040 49:2f00 82:0068 83:5060 84:4000 85:0000 86:1000 87:4000 88:407f 93:0000
[   49.431784] ata2: dev 0 ATA-6, max UDMA/133, 640 sectors: LBA
[   49.431910] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xffff810037fd8200
[   49.434347] ata2: dev 0 configured for UDMA/133

...

[   49.878231] SCSI device sdb: 640 512-byte hdwr sectors (0 MB)
[   49.878243] SCSI device sdb: drive cache: write through
[   49.878268] SCSI device sdb: 640 512-byte hdwr sectors (0 MB)
[   49.878278] SCSI device sdb: drive cache: write through
[   49.878279]  sdb: unknown partition table
[   49.880441] sd 1:0:0:0: Attached scsi disk sdb

```

As expected, the JMicron JMB363 controller doesn't work in Dapper so I tried compiling a 2.6.18 kernel. Using that, the ghost sdb device causes a very long hang on startup with error messages like these:

```

[   46.809899] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   76.738854] ata2.00: qc timeout (cmd 0xec)
[   76.738859] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x104)
[   84.572931] ata2: port is slow to respond, please be patient
[  107.483495] ata2: port failed to respond (30 secs)
[  107.483530] ata2: COMRESET failed (device not ready)
[  107.483563] ata2: hardreset failed, retrying in 5 secs
[  113.342965] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  113.343025] ata2.00: ATA-6, max UDMA/133, 640 sectors: LBA 
[  113.343028] ata2.00: ata2: dev 0 multi count 1
[  113.877358] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  113.877362] ata2.00: revalidation failed (errno=-5)
[  113.877405] ata2.00: limiting speed to PIO0
[  113.877406] ata2: failed to recover some devices, retrying in 5 secs
[  119.171943] ata2: SATA link down (SStatus 0 SControl 300)
[  119.171948] ata2.00: disabled
[  119.671943] scsi2 : ahci

```

It takes minutes to boot if it does at all. What's more, the JMicron controller still doesn't work. With 2.6.18 it is not even detected unless it's in AHCI mode, if it's AHCI or if I use 2.6.18.1 in either basic or AHCI, booting takes even longer and usually doesn't even go through. If it does, the drives connected to the JMicron don't work because anything I do with them just hangs and gives lost interrupts in dmesg.

Looks like the mysterious ata2 has something to do with the problem, but it still shows if I disable JMicron in bios so I guess it can't be the JMicron SATA plug (which is unused). I have also flashed my mobo with the newest BIOS, no change. Today I also tried Sabayon 3.1 which has 2.6.18, it behaves the same way: the ata2 timeouts on it, JMicron not working in basic mode, in AHCI mode I can't boot.

Any clues? Google turned up no help. Windows works without issues so far, but I'd rather not use it for anything else than games :(

---

