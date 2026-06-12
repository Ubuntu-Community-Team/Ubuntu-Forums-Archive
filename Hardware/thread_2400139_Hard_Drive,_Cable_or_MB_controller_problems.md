---
title: "Hard Drive, Cable or MB controller problems?"
date: 2018-09-03
forum: Hardware
---

### Post by Harpz on 2018-09-03
Hi

A couple of days ago I added a few drives from an old system to my server and an issue i had a few years ago has come back, last time it went away on its own and i never did get to the bottom of it.

This time i plan to, I'm guessing one the drives i have recently added is having issues or an SATA cable has broken down?

Whats the best way to map the drives ata assignment to it's /dev/sdX assignment so i can check ifs one of the drives i added?

Currently running Ubuntu Server 16.04.5 LTS and wanted get this sorted before i think about upgrading to the latest LTS.

```

Sep  2 22:59:07 Altair kernel: [359556.794739] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:07 Altair kernel: [359556.797220] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:07 Altair kernel: [359556.799632] ata7: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:07 Altair kernel: [359556.802026] ata7: hard resetting link
Sep  2 22:59:11 Altair kernel: [359561.057421] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  2 22:59:11 Altair kernel: [359561.059117] ata7.00: configured for UDMA/133
Sep  2 22:59:11 Altair kernel: [359561.059124] ata7: EH complete
Sep  2 22:59:12 Altair kernel: [359561.377818] ata8: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:12 Altair kernel: [359561.380305] ata8: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:12 Altair kernel: [359561.382835] ata8: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:12 Altair kernel: [359561.385410] ata8: hard resetting link
Sep  2 22:59:22 Altair kernel: [359571.389864] ata8: softreset failed (1st FIS failed)
Sep  2 22:59:22 Altair kernel: [359571.392438] ata8: hard resetting link
Sep  2 22:59:22 Altair kernel: [359571.728787] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:22 Altair kernel: [359571.731832] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:22 Altair kernel: [359571.734732] ata7: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:22 Altair kernel: [359571.737826] ata7: hard resetting link
Sep  2 22:59:26 Altair kernel: [359575.942112] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  2 22:59:26 Altair kernel: [359575.962276] ata7.00: configured for UDMA/133
Sep  2 22:59:26 Altair kernel: [359575.962291] ata7: EH complete
Sep  2 22:59:27 Altair kernel: [359576.630170] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  2 22:59:27 Altair kernel: [359576.652941] ata8.00: configured for UDMA/133
Sep  2 22:59:27 Altair kernel: [359576.652949] ata8: EH complete
Sep  2 22:59:28 Altair kernel: [359577.381266] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:28 Altair kernel: [359577.384351] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:28 Altair kernel: [359577.387219] ata7: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:28 Altair kernel: [359577.389944] ata7: hard resetting link
Sep  2 22:59:28 Altair kernel: [359578.037832] ata8: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:28 Altair kernel: [359578.040647] ata8: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:28 Altair kernel: [359578.043492] ata8: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:28 Altair kernel: [359578.046538] ata8: hard resetting link
Sep  2 22:59:32 Altair kernel: [359581.646442] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  2 22:59:32 Altair kernel: [359581.648230] ata7.00: configured for UDMA/133
Sep  2 22:59:32 Altair kernel: [359581.648271] ata7: EH complete
Sep  2 22:59:33 Altair kernel: [359582.302504] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  2 22:59:33 Altair kernel: [359582.304180] ata8.00: configured for UDMA/133
Sep  2 22:59:33 Altair kernel: [359582.304187] ata8: EH complete
Sep  2 22:59:33 Altair kernel: [359582.662278] ata8: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:33 Altair kernel: [359582.665383] ata8: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:33 Altair kernel: [359582.668568] ata8: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:33 Altair kernel: [359582.671839] ata8: hard resetting link
Sep  2 22:59:34 Altair kernel: [359583.268887] ata7: limiting SATA link speed to 1.5 Gbps
Sep  2 22:59:34 Altair kernel: [359583.268895] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:34 Altair kernel: [359583.272071] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:34 Altair kernel: [359583.275415] ata7: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:34 Altair kernel: [359583.278682] ata7: hard resetting link
Sep  2 22:59:37 Altair kernel: [359586.886809] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  2 22:59:37 Altair kernel: [359586.903907] ata8.00: configured for UDMA/133
Sep  2 22:59:37 Altair kernel: [359586.903917] ata8: EH complete
Sep  2 22:59:38 Altair kernel: [359587.482775] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  2 22:59:38 Altair kernel: [359587.508284] ata7.00: configured for UDMA/133
Sep  2 22:59:38 Altair kernel: [359587.508294] ata7: EH complete
Sep  2 22:59:38 Altair kernel: [359588.081345] ata8: limiting SATA link speed to 1.5 Gbps
Sep  2 22:59:38 Altair kernel: [359588.081355] ata8: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
Sep  2 22:59:38 Altair kernel: [359588.084760] ata8: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:38 Altair kernel: [359588.088131] ata8: SError: { RecovComm Persist PHYRdyChg 10B8B }
Sep  2 22:59:38 Altair kernel: [359588.091376] ata8: hard resetting link
Sep  2 22:59:40 Altair kernel: [359589.874640] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
Sep  2 22:59:40 Altair kernel: [359589.878020] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:40 Altair kernel: [359589.881438] ata7: SError: { Persist PHYRdyChg 10B8B }
Sep  2 22:59:40 Altair kernel: [359589.884857] ata7: hard resetting link
Sep  2 22:59:43 Altair kernel: [359592.302964] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  2 22:59:43 Altair kernel: [359592.325474] ata8.00: configured for UDMA/133
Sep  2 22:59:43 Altair kernel: [359592.325482] ata8: EH complete
Sep  2 22:59:43 Altair kernel: [359592.908064] ata8: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
Sep  2 22:59:43 Altair kernel: [359592.911533] ata8: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:43 Altair kernel: [359592.915094] ata8: SError: { Persist PHYRdyChg 10B8B }
Sep  2 22:59:43 Altair kernel: [359592.918442] ata8: hard resetting link
Sep  2 22:59:44 Altair kernel: [359594.091061] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  2 22:59:44 Altair kernel: [359594.097695] ata7.00: configured for UDMA/133
Sep  2 22:59:44 Altair kernel: [359594.097706] ata7: EH complete
Sep  2 22:59:53 Altair kernel: [359602.919505] ata8: softreset failed (1st FIS failed)
Sep  2 22:59:53 Altair kernel: [359602.922758] ata8: hard resetting link
Sep  2 22:59:54 Altair kernel: [359604.027760] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
Sep  2 22:59:54 Altair kernel: [359604.030992] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:54 Altair kernel: [359604.034246] ata7: SError: { Persist PHYRdyChg 10B8B }
Sep  2 22:59:54 Altair kernel: [359604.037405] ata7: hard resetting link
Sep  2 22:59:58 Altair kernel: [359608.139747] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  2 22:59:58 Altair kernel: [359608.144204] ata8.00: configured for UDMA/133
Sep  2 22:59:58 Altair kernel: [359608.144242] ata8: EH complete
Sep  2 22:59:58 Altair kernel: [359608.243760] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  2 22:59:58 Altair kernel: [359608.263514] ata7.00: configured for UDMA/133
Sep  2 22:59:58 Altair kernel: [359608.263521] ata7: EH complete
Sep  2 22:59:59 Altair kernel: [359608.792450] ata8: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
Sep  2 22:59:59 Altair kernel: [359608.795758] ata8: irq_stat 0x00400000, PHY RDY changed
Sep  2 22:59:59 Altair kernel: [359608.798923] ata8: SError: { Persist PHYRdyChg 10B8B }
Sep  2 22:59:59 Altair kernel: [359608.802185] ata8: hard resetting link
Sep  2 23:00:01 Altair kernel: [359610.640735] ata7: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
Sep  2 23:00:01 Altair kernel: [359610.644020] ata7: irq_stat 0x00400000, PHY RDY changed
Sep  2 23:00:01 Altair kernel: [359610.647238] ata7: SError: { Persist PHYRdyChg 10B8B }
Sep  2 23:00:01 Altair kernel: [359610.650465] ata7: hard resetting link

```

---

### Post by SeijiSensei on 2018-09-03
The command "sudo blkid" will list any partitions found on all drives.  On this machine I get the following:

```

dev/sdb7: UUID="415c3465-fca1-4660-970e-91198c0889f2" TYPE="ext4" PARTUUID="fb4ac0b6-07"
/dev/sda1: UUID="7d5eb78b-9387-031d-01c4-2ba3dd74ca7e" UUID_SUB="c2148191-4541-70ec-7da5-5c49992d2773" LABEL="linux-tv:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="033f7f89-531e-495e-8357-95f5272f2ed4"
/dev/sdb1: UUID="44f3b810-50e3-48dd-9880-ca18d86b9c19" TYPE="ext2" PARTUUID="fb4ac0b6-01"
/dev/sdb2: LABEL="Recovery" UUID="E414794C147922AA" TYPE="ntfs" PARTUUID="fb4ac0b6-02"
/dev/sdb3: LABEL="WIN7" UUID="1E1E81AF1E81808F" TYPE="ntfs" PARTUUID="fb4ac0b6-03"
/dev/sdb5: LABEL="HOME" UUID="5ad2f16e-6c75-46c2-85de-dc101803ae91" TYPE="ext4" PARTUUID="fb4ac0b6-05"
/dev/sdb6: UUID="bba56ea0-3677-4846-957d-5c57a1927805" TYPE="swap" PARTUUID="fb4ac0b6-06"
/dev/sdb8: LABEL="ROOT2" UUID="c3692961-e675-464d-8441-ac54da0f60a6" TYPE="ext4" PARTUUID="fb4ac0b6-08"
/dev/sdb9: LABEL="GAMES" UUID="29960BAF271E9A69" TYPE="ntfs" PTTYPE="dos" PARTUUID="fb4ac0b6-09"
/dev/sdc1: UUID="7d5eb78b-9387-031d-01c4-2ba3dd74ca7e" UUID_SUB="93f5497e-447a-8576-ad51-93f77192e162" LABEL="linux-tv:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="5962c4c1-da6d-4f68-a196-8d65082a23cb"
/dev/md0: LABEL="RAID" UUID="ff2902fb-c4bc-41a4-bd94-72bedf5eec32" TYPE="ext4"

```

My boot device happens to be /dev/sdb because of how my drives are enumerated.

I'm not sure any of this will help though.  Those disks are throwing hardware errors and may be irretrievable.

---

### Post by oldfred on 2018-09-03
What brand motherboard?

Some have Asmedia ports in addition to the standard Intel ports and those are not supported.

---

### Post by Harpz on 2018-09-03
Hi oldfred

The motherboard is an Asus M5A78L-M LX V2 does this make a difference?

---

### Post by oldfred on 2018-09-03
Do not know spec of that motherboard. Does manual mention Asmedia anywhere?

I know issue is common with Asrock Intel based motherboards that have extra ports that then are the Asmedia.

If you plug a non-working drive into a known working port does it then work. 
Or exchange cables to see if a cable issue.

---

### Post by Harpz on 2018-09-03
I do have an ASMedia  ASM1062 Serial ATA Controller but that has never thrown an error or been an issue that i'm aware of, my boot drive is attached to it along with one of my parity drives for SnapRAID.

The drives throwing the errors are attached to the motherboard.

 *-storage
       description: SATA controller
       product: ASM1062 Serial ATA Controller
       vendor: ASMedia Technology Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
       configuration: driver=ahci latency=0
       resources: irq:27 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=32) memory:febffc00-febffdff memory:febe0000-febeffff

Going to see if changing the SATA cables helps, just hoping its not a problem with the 3x X-Case 5in3 caddy these drives are in.

---

### Post by oldfred on 2018-09-04
There also can be UEFI/BIOS settings for drives.
One of my motherboard has two groups and another has each drive with settings.
There even are settings to turn drive off with some systems, so make sure settings show drives in UEFI.

---

