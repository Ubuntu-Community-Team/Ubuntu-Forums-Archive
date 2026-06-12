---
title: "Compact Flash is automounted only if inserted after Ipod"
date: 2009-06-05
forum: Hardware
---

### Post by karlosmhr on 2009-06-05
I have a Compact Flash card (using PCMCIA adapter), when plugged under 8.04 Live CD, It got auto mounted ok.

So I decided to install 8.04, after installing, then plugged compact flash, but got a message: Invalid mount option then attempting to mount the volume 'XXXXXX'. So I updated/upgraded via apt, restart, but problem persists.

For other reason I plugged my ipod, and then plug my compact flash, suddenly the compact flash card got auto mounted properly.

I have tested the environment several times:
A) plug compact flash = **Invalid mount message**
B) ipod -> plug compact flash = **auto mount compact flash ok**

I searched for this "behavior" at ubuntuforums but didn't found a solution.

I need to use my compact flash without need to plug my ipod before, so if somebody knows or could find a workaround for this I have the messages at each case:
**A)**
[I]Jun  4 22:41:48 laptop kernel: [ 4401.838798] pccard: PCMCIA card inserted into slot 0
Jun  4 22:41:48 laptop kernel: [ 4401.839896] pcmcia: registering new device pcmcia0.0
Jun  4 22:41:48 laptop kernel: [ 4401.887450] scsi18 : pata_pcmcia
Jun  4 22:41:48 laptop kernel: [ 4401.888069] ata14: PATA max PIO0 cmd 0x3100 ctl 0x310e irq 3
Jun  4 22:41:48 laptop kernel: [ 4402.058983] ata14.00: CFA: STI Flash 8.0.0, 01/17/07, max MWDMA2
Jun  4 22:41:48 laptop kernel: [ 4402.058991] ata14.00: 1000944 sectors, multi 0: LBA 
Jun  4 22:41:48 laptop kernel: [ 4402.066956] ata14.00: configured for PIO0
Jun  4 22:41:48 laptop kernel: [ 4402.090957] ata14.00: configured for PIO0
Jun  4 22:41:48 laptop kernel: [ 4402.090969] ata14: EH complete
Jun  4 22:41:48 laptop kernel: [ 4402.091516] scsi 18:0:0:0: Direct-Access     ATA      STI Flash 8.0.0  01/1 PQ: 0 ANSI: 5
Jun  4 22:41:48 laptop kernel: [ 4402.092284] sd 18:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
Jun  4 22:41:48 laptop kernel: [ 4402.092593] sd 18:0:0:0: [sdb] Write Protect is off
Jun  4 22:41:48 laptop kernel: [ 4402.092961] sd 18:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  4 22:41:48 laptop kernel: [ 4402.093353] sd 18:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
Jun  4 22:41:48 laptop kernel: [ 4402.093610] sd 18:0:0:0: [sdb] Write Protect is off
Jun  4 22:41:48 laptop kernel: [ 4402.093969] sd 18:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  4 22:41:48 laptop kernel: [ 4402.094232]  sdb: sdb1
Jun  4 22:41:48 laptop kernel: [ 4402.100386] sd 18:0:0:0: [sdb] Attached SCSI removable disk
Jun  4 22:41:48 laptop kernel: [ 4402.100998] sd 18:0:0:0: Attached scsi generic sg2 type 0
Jun  4 22:41:50 laptop kernel: [ 4403.480462] UDF-fs: No VRS found
Jun  4 22:41:50 laptop kernel: [ 4403.712871] ISOFS: Unable to identify CD-ROM format.[/I]
[B]
B)[/B]
[I]Jun  4 22:42:39 laptop kernel: [ 4452.676434] pccard: PCMCIA card inserted into slot 0
Jun  4 22:42:39 laptop kernel: [ 4452.677517] pcmcia: registering new device pcmcia0.0
Jun  4 22:42:39 laptop kernel: [ 4452.728654] scsi20 : pata_pcmcia
Jun  4 22:42:39 laptop kernel: [ 4452.729287] ata15: PATA max PIO0 cmd 0x3100 ctl 0x310e irq 3
Jun  4 22:42:39 laptop kernel: [ 4452.900591] ata15.00: CFA: STI Flash 8.0.0, 01/17/07, max MWDMA2
Jun  4 22:42:39 laptop kernel: [ 4452.900599] ata15.00: 1000944 sectors, multi 0: LBA 
Jun  4 22:42:39 laptop kernel: [ 4452.908594] ata15.00: configured for PIO0
Jun  4 22:42:39 laptop kernel: [ 4452.932567] ata15.00: configured for PIO0
Jun  4 22:42:39 laptop kernel: [ 4452.932580] ata15: EH complete
Jun  4 22:42:39 laptop kernel: [ 4452.933268] scsi 20:0:0:0: Direct-Access     ATA      STI Flash 8.0.0  01/1 PQ: 0 ANSI: 5
Jun  4 22:42:39 laptop kernel: [ 4452.934086] sd 20:0:0:0: [sdc] 1000944 512-byte hardware sectors (512 MB)
Jun  4 22:42:39 laptop kernel: [ 4452.934397] sd 20:0:0:0: [sdc] Write Protect is off
Jun  4 22:42:39 laptop kernel: [ 4452.934770] sd 20:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  4 22:42:39 laptop kernel: [ 4452.935135] sd 20:0:0:0: [sdc] 1000944 512-byte hardware sectors (512 MB)
Jun  4 22:42:39 laptop kernel: [ 4452.935389] sd 20:0:0:0: [sdc] Write Protect is off
Jun  4 22:42:39 laptop kernel: [ 4452.935749] sd 20:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  4 22:42:39 laptop kernel: [ 4452.936041]  sdc: sdc1
Jun  4 22:42:39 laptop kernel: [ 4452.942495] sd 20:0:0:0: [sdc] Attached SCSI removable disk
Jun  4 22:42:39 laptop kernel: [ 4452.943103] sd 20:0:0:0: Attached scsi generic sg3 type 0[/I]

Thanks in Advance

Karlos

---

