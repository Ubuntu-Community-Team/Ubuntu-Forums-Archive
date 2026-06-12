---
title: "Firefox and system hangs"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by kranny on 2009-01-07
Hi..After a couple of system freezes (when i changed my hard drive to another system)i had to have a fresh install of hardy on my drive..But the problem still persists..Its not a crash and just a freeze..Never faced this problem before in my 8 months usage of hardy.

Firefox hangs for every 2 min and system hangs for every 10 min
My dmesg output:
[ 2354.179996] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
[ 2354.180008] ata1: SError: { 10B8B Dispar }
[ 2354.180018] ata1.00: cmd ca/00:08:a2:f1:18/00:00:00:00:00/ef tag 0 dma 4096 out
[ 2354.180021] res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2354.180026] ata1.00: status: { DRDY }
[ 2359.529982] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 2364.232235] ata1: device not ready (errno=-16), forcing hardreset
[ 2364.232245] ata1: hard resetting link
[ 2364.708070] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2364.821816] ata1.00: configured for UDMA/133
[ 2364.821834] ata1: EH complete
[ 2364.846349] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 2364.846457] sd 0:0:0:0: [sda] Write Protect is off
[ 2364.846462] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2364.846772] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by kranny on 2009-01-07
Problem solved to some extentediting /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

Now the freezes occur in long intervals:D:D

---

### Post by kranny on 2009-01-08
Waiting for a reply:(

---

