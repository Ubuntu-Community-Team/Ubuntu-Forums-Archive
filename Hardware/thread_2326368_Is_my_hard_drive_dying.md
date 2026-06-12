---
title: "Is my hard drive dying?"
date: 2016-05-31
forum: Hardware
---

### Post by jonny3010 on 2016-05-31
Hi All,

I got 6 WD Reds in ZFS raid. 2 sets of 3 drives in raidz1. Data is ok, just running a scrub to make sure.

I'm getting these errors for ata10 on boot (dmesg) which is putting the drive in 1.5gbps. Also its setting ata20 in 1.5gbps but there is no drive for ata20.
I took at look at S.M.A.R.T for the drive but it says no errors, but the log says different.

SEE LOG BELOW.

```

[FONT=arial][    3.313081] ata3: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=arial][    3.313115] ata6: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=arial][    3.313149] ata2: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=arial][    3.317090] ata8: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=arial][    3.321073] ata7: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=arial][    3.333088] ata12: SATA link down (SStatus 0 SControl 300)[/FONT]
[FONT=arial][    3.353084] ata20: SATA link up 1.5 Gbps (SStatus 113 SControl 300)[/FONT]
[FONT=arial][    3.365104] ata19: SATA link down (SStatus 0 SControl 310)[/FONT]
[FONT=arial][    3.365138] ata15: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.365167] ata16: SATA link down (SStatus 0 SControl 310)[/FONT]
[FONT=arial][    3.365199] ata17: SATA link down (SStatus 0 SControl 310)[/FONT]
[FONT=arial][    3.369077] ata18: SATA link down (SStatus 0 SControl 310)[/FONT]
[FONT=arial][    3.493070] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.497074] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.497718] ata4.00: ATA-9: WDC WD10JFCX-68N6GN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.497725] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.498409] ata4.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.501071] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.501073] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.501647] ata10.00: ATA-9: WDC WD30EFRX-68EUZN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.501655] ata10.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.501737] ata5.00: ATA-9: WDC WD10JFCX-68N6GN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.501740] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.502370] ata5.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.504750] ata1.00: ATA-8: OCZ-AGILITY3, 2.22, max UDMA/133[/FONT]
[FONT=arial][    3.504754] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.505101] ata9: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.505650] ata9.00: ATA-9: WDC WD30EFRX-68EUZN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.505657] ata9.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.506198] ata9.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.509070] ata11: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.509592] ata11.00: ATA-9: WDC WD30EFRX-68EUZN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.509599] ata11.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.510146] ata11.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.515117] ata1.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.533088] ata13: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.703266] ata20.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66[/FONT]
[FONT=arial][    3.703397] ata20.00: configured for UDMA/66[/FONT]
[FONT=arial][    3.704222] ata13.00: ATA-9: WDC WD30EFRX-68EUZN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.704230] ata13.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.704240] ata15.00: ATA-9: WDC WD30EFRX-68EUZN0, 82.00A82, max UDMA/133[/FONT]
[FONT=arial][    3.704249] ata15.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.705241] ata13.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.705260] ata15.00: configured for UDMA/133[/FONT]
[FONT=arial][    3.757104] ata14: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][    3.757884] ata14.00: ATA-9: WDC WD30EFRX-68EUZN0, 80.00A80, max UDMA/133[/FONT]
[FONT=arial][    3.757918] ata14.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA[/FONT]
[FONT=arial][    3.758744] ata14.00: configured for UDMA/133[/FONT]
[FONT=arial][    8.501060] ata10.00: qc timeout (cmd 0xef)[/FONT]
[FONT=arial][    8.501087] ata10.00: failed to enable AA (error_mask=0x4)[/FONT]
[FONT=arial][    8.501113] ata10.00: revalidation failed (errno=-5)[/FONT]
[FONT=arial][    8.993069] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/FONT]
[FONT=arial][   13.993041] ata10.00: qc timeout (cmd 0x27)[/FONT]
[FONT=arial][   13.993067] ata10.00: failed to read native max address (err_mask=0x4)[/FONT]
[FONT=arial][   13.993096] ata10.00: HPA support seems broken, skipping HPA handling[/FONT]
[FONT=arial][   13.993125] ata10.00: revalidation failed (errno=-5)[/FONT]
[FONT=arial][   13.993150] ata10: limiting SATA link speed to 3.0 Gbps[/FONT]
[FONT=arial][   13.993178] ata10.00: limiting speed to UDMA/133:PIO3[/FONT]
[FONT=arial][   14.485043] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 320)[/FONT]
[FONT=arial][   14.486054] ata10.00: configured for UDMA/133[/FONT]
[FONT=arial][   15.094126] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)[/FONT]
[FONT=arial][   15.357207] systemd[1]: Listening on LVM2 metadata daemon socket.[/FONT]
[FONT=arial][   41.388979] ata10.00: exception Emask 0x10 SAct 0x70 SErr 0x400000 action 0x6 frozen[/FONT]
[FONT=arial][   41.390347] ata10.00: irq_stat 0x08000000, interface fatal error[/FONT]
[FONT=arial][   41.391635] ata10: SError: { Handshk }[/FONT]
[FONT=arial][   41.392935] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   41.394483] ata10.00: cmd 61/10:20:10:0a:00/00:00:00:00:[/FONT][FONT=arial]00/40 tag 4 ncq 8192 out[/FONT]
[FONT=arial][   41.397599] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   41.399093] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   41.400571] ata10.00: cmd 61/10:28:10:5c:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 5 ncq 8192 out[/FONT]
[FONT=arial][   41.403616] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   41.405121] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   41.406612] ata10.00: cmd 61/10:30:10:5e:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 6 ncq 8192 out[/FONT]
[FONT=arial][   41.409679] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   41.411164] ata10: hard resetting link[/FONT]
[FONT=arial][   41.900968] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 320)[/FONT]
[FONT=arial][   41.901815] ata10.00: configured for UDMA/133[/FONT]
[FONT=arial][   41.901826] ata10: EH complete[/FONT]
[FONT=arial][   41.908971] ata10.00: exception Emask 0x10 SAct 0x700 SErr 0x400000 action 0x6 frozen[/FONT]
[FONT=arial][   41.910284] ata10.00: irq_stat 0x08000000, interface fatal error[/FONT]
[FONT=arial][   41.911540] ata10: SError: { Handshk }[/FONT]
[FONT=arial][   41.912785] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   41.914052] ata10.00: cmd 61/10:40:10:5e:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 8 ncq 8192 out[/FONT]
[FONT=arial][   41.917139] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   41.918648] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   41.920138] ata10.00: cmd 61/10:48:10:5c:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 9 ncq 8192 out[/FONT]
[FONT=arial][   41.923190] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   41.924689] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   41.926191] ata10.00: cmd 61/10:50:10:0a:00/00:00:00:00:[/FONT][FONT=arial]00/40 tag 10 ncq 8192 out[/FONT]
[FONT=arial][   41.929291] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   41.930829] ata10: hard resetting link[/FONT]
[FONT=arial][   42.420966] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 320)[/FONT]
[FONT=arial][   42.421875] ata10.00: configured for UDMA/133[/FONT]
[FONT=arial][   42.421883] ata10: EH complete[/FONT]
[FONT=arial][   42.428969] ata10.00: exception Emask 0x10 SAct 0xe00000 SErr 0x400000 action 0x6 frozen[/FONT]
[FONT=arial][   42.430328] ata10.00: irq_stat 0x08000000, interface fatal error[/FONT]
[FONT=arial][   42.431648] ata10: SError: { Handshk }[/FONT]
[FONT=arial][   42.432978] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   42.434573] ata10.00: cmd 61/10:a8:10:0a:00/00:00:00:00:[/FONT][FONT=arial]00/40 tag 21 ncq 8192 out[/FONT]
[FONT=arial][   42.437878] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   42.439503] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   42.441121] ata10.00: cmd 61/10:b0:10:5c:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 22 ncq 8192 out[/FONT]
[FONT=arial][   42.444404] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   42.446038] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   42.447703] ata10.00: cmd 61/10:b8:10:5e:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 23 ncq 8192 out[/FONT]
[FONT=arial][   42.451117] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   42.452787] ata10: hard resetting link[/FONT]
[FONT=arial][   42.940963] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 320)[/FONT]
[FONT=arial][   42.941856] ata10.00: configured for UDMA/133[/FONT]
[FONT=arial][   42.941867] ata10: EH complete[/FONT]
[FONT=arial][   42.948967] ata10: limiting SATA link speed to 1.5 Gbps[/FONT]
[FONT=arial][   42.948970] ata10.00: exception Emask 0x10 SAct 0x30 SErr 0x400000 action 0x6 frozen[/FONT]
[FONT=arial][   42.950430] ata10.00: irq_stat 0x08000000, interface fatal error[/FONT]
[FONT=arial][   42.951846] ata10: SError: { Handshk }[/FONT]
[FONT=arial][   42.953268] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   42.955001] ata10.00: cmd 61/10:20:10:5c:50/00:00:5d:01:[/FONT][FONT=arial]00/40 tag 4 ncq 8192 out[/FONT]
[FONT=arial][   42.958473] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   42.960181] ata10.00: failed command: WRITE FPDMA QUEUED[/FONT]
[FONT=arial][   42.961875] ata10.00: cmd 61/10:28:10:0a:00/00:00:00:00:[/FONT][FONT=arial]00/40 tag 5 ncq 8192 out[/FONT]
[FONT=arial][   42.965318] ata10.00: status: { DRDY }[/FONT]
[FONT=arial][   42.967078] ata10: hard resetting link[/FONT]
[FONT=arial][   43.456962] ata10: SATA link up 1.5 Gbps (SStatus 113 SControl 310)[/FONT]
[FONT=arial][   43.457936] ata10.00: configured for UDMA/133[/FONT]
[FONT=arial][   43.457945] ata10: EH complete[/FONT]
[FONT=arial][  356.753710] ata20.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6[/FONT]
[FONT=arial][  356.753846] ata20.00: irq_stat 0x40000001[/FONT]
[FONT=arial][  356.753940] ata20.00: cmd a0/01:00:00:00:01/00:00:00:00:[/FONT][FONT=arial]00/a0 tag 4 dma 16640 in[/FONT]
[FONT=arial][  356.754246] ata20: hard resetting link[/FONT]
[FONT=arial][  357.081701] ata20: SATA link up 1.5 Gbps (SStatus 113 SControl 300)[/FONT]
[FONT=arial][  357.081953] ata20.00: configured for UDMA/66[/FONT]
[FONT=arial][  357.082052] ata20: EH complete[/FONT]
[FONT=arial][  357.097636] ata20.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6[/FONT]
[FONT=arial][  357.097769] ata20.00: irq_stat 0x40000001[/FONT]
[FONT=arial][  357.097864] ata20.00: cmd a0/01:00:00:00:01/00:00:00:00:[/FONT][FONT=arial]00/a0 tag 5 dma 16640 in[/FONT]
[FONT=arial][  357.098179] ata20: hard resetting link[/FONT]
[FONT=arial][  357.425646] ata20: SATA link up 1.5 Gbps (SStatus 113 SControl 300)[/FONT]
[FONT=arial][  357.425928] ata20.00: configured for UDMA/66[/FONT]
[FONT=arial][  357.426035] ata20: EH complete[/FONT]
[FONT=arial]root@WinterFell:/home/jonny# ls -l /sys/block/sd* | sed 's/.*\(sd.*\) -.*\(ata.*\)\/h.*/\2 => \1/'[/FONT]
[FONT=arial]ata1 => sda[/FONT]
[FONT=arial]ata4 => sdb[/FONT]
[FONT=arial]ata5 => sdc[/FONT]
[FONT=arial]ata9 => sdd[/FONT]
[FONT=arial]ata10 => sde[/FONT]
[FONT=arial]ata11 => sdf[/FONT]
[FONT=arial]ata13 => sdg[/FONT]
[FONT=arial]ata14 => sdh[/FONT]
[FONT=arial]ata15 => sdi[/FONT]
[FONT=arial]root@WinterFell:/home/jonny#[/FONT]
```

---

### Post by houstonbofh on 2016-05-31
Start with looking at the smart values on the drive.  Lots of things can cause read errors.  (Like bad SATA cables)

---

### Post by jonny3010 on 2016-05-31
> **houstonbofh said:**
> Start with looking at the smart values on the drive.  Lots of things can cause read errors.  (Like bad SATA cables)
Thanks.

Did a long self test came back fine.
reseated PCI card, and sata cables, all is fine now. was working fine for months until I changed out the graphics card this weekend, must have nocked a cable.

Still got something connecting at 1.5 GBPS to on ata20 which is on my Marvell Sata PCI Card. I got 3 hdds on that controller and they show up along with this random device on ata20. but it does not have a sdX id for it. Very strange

---

