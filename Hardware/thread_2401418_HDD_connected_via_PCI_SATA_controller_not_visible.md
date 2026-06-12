---
title: "HDD connected via PCI SATA controller not visible"
date: 2018-09-18
forum: Hardware
---

### Post by gordan.cuic on 2018-09-18
I can't see HDD connected to PCI SATA controller. Any ideas why? Or what should I check?

Background:
I have Ubuntu server running on Gigabyte GA-Z-78P-D3 MBO. That board has 6 SATA connectors available. Till now, I've used 5 of them: 1 SSD with ubuntu installation and 4 of them for RAID10 array. I needed additional 2 disks, so I connected one WD RED into 6th MBO SATA slot, and the other one to SATA PCI Card. It was my understanding that no driver installation would be necessary - just plug in, start the server and both disks should be visible via ```
lsblk
``` or ```
cat /proc/scsi/scsi
```
But those commands don't show disk connected via PCI controller. (see atth for result).
[ATTACH=CONFIG]281114[/ATTACH][ATTACH=CONFIG]281115[/ATTACH]

Ubuntu 18.04.1 LTS (server)
MBO: Gigabyte GA-Z-78P-D3
PCI SATA controller: VIA Technologies, Inc. VT6421 IDE/SATA Controller (rev 50)

MBO SATA:
sda (KINGSTON SSD SV300S3 111 GB, ubuntu server instalation)
sdb, sdc, sdd, sde (WD Black WD1003FZEX-0 in RAID 10, mounted to /mnt/md0/, data)
sdf (new disk 1/2, WD Red WD80EFAX-68K, another data disk, not mounted yet)

PCI SATA;
new disk 2/2, WD Red WD80EFAX-68K - not visible

---

### Post by Yellow Pasque on 2018-09-19
Does it show in BIOS/EFI? Any clues in dmesg?

---

