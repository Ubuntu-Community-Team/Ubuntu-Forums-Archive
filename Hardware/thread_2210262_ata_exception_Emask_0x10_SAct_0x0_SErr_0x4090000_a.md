---
title: "ata: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen"
date: 2014-03-09
forum: Hardware
---

### Post by jason63 on 2014-03-09
Ubuntu Server 13.04 or something 

[COLOR=#000000]Asus H87 MB[/COLOR]
[COLOR=#000000]Intel i5-4570 [/COLOR]
[COLOR=#000000]16gb Ram[/COLOR]
[COLOR=#000000]Corsair hx750 psu

[/COLOR][COLOR=#000000]1x 36gb Raptor (OS on motherboard sata controller)
[/COLOR]
[COLOR=#000000]/dev/md0 = 4x 200gb sata (Raid 0 on motherboard sata controller)
[/COLOR]
/dev/md1 = 2x 36gb Raptor (Raid 0 on 2 port sata card)

[COLOR=#000000]/dev/md2 = 2x 320gb sata (Raid 0 on 4 port pci sata card)[/COLOR]
[COLOR=#000000]/dev/md3 = 2x 160gb sata (Raid 0 on same pci-e sata card)[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]

[/COLOR]Speeds over GBE (windows SMB server)

Sustains over 95 MB/s to  /dev/md0  (4x 200GB raid 0)
Sustains over 95 MB/s to /dev/md1  (2x 36GB raptor raid 0)
Average 65 MB/s to  /dev/md2  (2x 320GB raptor raid 0)
Average 65 MB/s to  /dev/md3  (2x 160GB raptor raid 0)

Each RAID set is together on the same controller

This server isnt used for anything yet. I'm waiting  on 6x WD40EFRX RED drives to come in, so Im playing with spare Sata hard drives and controllers I have lying around.

Now heres the problem, every few hours, for no reason, even at idle I get this error in my /var/log/kern.log


```
[COLOR=#393939]Mar  9 21:48:17 BACKUP kernel: [345819.226066] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen[/COLOR]Mar  9 21:48:17 BACKUP kernel: [345819.227096] ata5: irq_stat 0x00400040, connection status changed
Mar  9 21:48:17 BACKUP kernel: [345819.227914] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  9 21:48:17 BACKUP kernel: [345819.228649] ata5: hard resetting link
Mar  9 21:48:21 BACKUP kernel: [345823.028972] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 21:48:21 BACKUP kernel: [345823.036894] ata5.00: configured for UDMA/133 [COLOR=#393939]Mar  9 21:48:21 BACKUP kernel: [345823.036897] ata5: EH complete[/COLOR]
```

Some times in 3 hours, a few times it was within 30 minutes. Usually when the server isn't being used. Its even happened a few times when I wasn't home and the only thing the machine was doing was idling. Ive tried reproducing the error by copying files to each of the drives, streaming movies and music off them etc but to no avail.

Heres an example where it happened repeatedly while I wasn't home and server wasn't in use at all.

```
[COLOR=#393939]Mar  7 10:38:06 BACKUP kernel: [136407.797235] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen[/COLOR]Mar  7 10:38:06 BACKUP kernel: [136407.800518] ata5: irq_stat 0x00400040, connection status changed
Mar  7 10:38:06 BACKUP kernel: [136407.803806] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  7 10:38:06 BACKUP kernel: [136407.807074] ata5: hard resetting link
Mar  7 10:38:09 BACKUP kernel: [136410.992729] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 10:38:09 BACKUP kernel: [136411.001063] ata5.00: configured for UDMA/133
Mar  7 10:38:09 BACKUP kernel: [136411.001073] ata5: EH complete
Mar  7 11:26:13 BACKUP kernel: [139294.892798] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  7 11:26:13 BACKUP kernel: [139294.896115] ata5: irq_stat 0x00400040, connection status changed
Mar  7 11:26:13 BACKUP kernel: [139294.899386] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  7 11:26:13 BACKUP kernel: [139294.902653] ata5: hard resetting link
Mar  7 11:26:17 BACKUP kernel: [139298.705976] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 11:26:17 BACKUP kernel: [139298.714302] ata5.00: configured for UDMA/133
Mar  7 11:26:17 BACKUP kernel: [139298.714312] ata5: EH complete
Mar  7 13:44:26 BACKUP kernel: [147588.501575] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  7 13:44:26 BACKUP kernel: [147588.504893] ata5: irq_stat 0x00400040, connection status changed
Mar  7 13:44:26 BACKUP kernel: [147588.508163] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  7 13:44:26 BACKUP kernel: [147588.511432] ata5: hard resetting link
Mar  7 13:44:30 BACKUP kernel: [147592.314065] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 13:44:30 BACKUP kernel: [147592.322401] ata5.00: configured for UDMA/133
Mar  7 13:44:30 BACKUP kernel: [147592.322411] ata5: EH complete
Mar  7 16:44:30 BACKUP kernel: [158391.973328] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  7 16:44:30 BACKUP kernel: [158391.974157] ata5: irq_stat 0x00400040, connection status changed
Mar  7 16:44:30 BACKUP kernel: [158391.974974] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  7 16:44:30 BACKUP kernel: [158391.975757] ata5: hard resetting link
Mar  7 16:44:34 BACKUP kernel: [158395.779706] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 16:44:34 BACKUP kernel: [158395.787638] ata5.00: configured for UDMA/133
Mar  7 16:44:34 BACKUP kernel: [158395.787641] ata5: EH complete
Mar  7 17:35:46 BACKUP kernel: [161468.461229] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  7 17:35:46 BACKUP kernel: [161468.464521] ata5: irq_stat 0x00400040, connection status changed
Mar  7 17:35:46 BACKUP kernel: [161468.467813] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  7 17:35:46 BACKUP kernel: [161468.471086] ata5: hard resetting link
Mar  7 17:35:50 BACKUP kernel: [161472.272829] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 17:35:50 BACKUP kernel: [161472.281060] ata5.00: configured for UDMA/133
Mar  7 17:35:50 BACKUP kernel: [161472.281070] ata5: EH complete
Mar  7 18:15:08 BACKUP kernel: [163830.023853] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  7 18:15:08 BACKUP kernel: [163830.027171] ata5: irq_stat 0x00400040, connection status changed
Mar  7 18:15:08 BACKUP kernel: [163830.030434] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  7 18:15:08 BACKUP kernel: [163830.033711] ata5: hard resetting link
Mar  7 18:15:12 BACKUP kernel: [163833.834576] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 18:15:12 BACKUP kernel: [163833.842919] ata5.00: configured for UDMA/133
Mar  7 18:15:12 BACKUP kernel: [163833.842930] ata5: EH complete
Mar  7 19:09:08 BACKUP kernel: [167069.886324] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  7 19:09:08 BACKUP kernel: [167069.889645] ata5: irq_stat 0x00400040, connection status changed
Mar  7 19:09:08 BACKUP kernel: [167069.892921] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  7 19:09:08 BACKUP kernel: [167069.896195] ata5: hard resetting link
Mar  7 19:09:12 BACKUP kernel: [167073.699485] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 19:09:12 BACKUP kernel: [167073.707818] ata5.00: configured for UDMA/133
Mar  7 19:09:12 BACKUP kernel: [167073.707828] ata5: EH complete
Mar  7 23:49:25 BACKUP kernel: [183887.452182] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  7 23:49:25 BACKUP kernel: [183887.452997] ata5: irq_stat 0x00400040, connection status changed
Mar  7 23:49:25 BACKUP kernel: [183887.453725] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  7 23:49:25 BACKUP kernel: [183887.454451] ata5: hard resetting link
Mar  7 23:49:29 BACKUP kernel: [183891.255390] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  7 23:49:29 BACKUP kernel: [183891.263301] ata5.00: configured for UDMA/133
Mar  7 23:49:29 BACKUP kernel: [183891.263304] ata5: EH complete
Mar  8 00:38:45 BACKUP kernel: [186847.104320] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 00:38:45 BACKUP kernel: [186847.107644] ata5: irq_stat 0x00400040, connection status changed
Mar  8 00:38:45 BACKUP kernel: [186847.110922] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 00:38:45 BACKUP kernel: [186847.114195] ata5: hard resetting link
Mar  8 00:38:49 BACKUP kernel: [186850.916601] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 00:38:49 BACKUP kernel: [186850.924950] ata5.00: configured for UDMA/133
Mar  8 00:38:49 BACKUP kernel: [186850.924960] ata5: EH complete
Mar  8 00:48:05 BACKUP kernel: [187406.623767] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  8 00:48:05 BACKUP kernel: [187406.627088] ata5: irq_stat 0x00400040, connection status changed
Mar  8 00:48:05 BACKUP kernel: [187406.630372] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  8 00:48:05 BACKUP kernel: [187406.633655] ata5: hard resetting link
Mar  8 00:48:08 BACKUP kernel: [187410.436092] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 00:48:08 BACKUP kernel: [187410.444421] ata5.00: configured for UDMA/133
Mar  8 00:48:08 BACKUP kernel: [187410.444431] ata5: EH complete
Mar  8 04:03:14 BACKUP kernel: [199116.258873] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 04:03:14 BACKUP kernel: [199116.262196] ata5: irq_stat 0x00400040, connection status changed
Mar  8 04:03:14 BACKUP kernel: [199116.265485] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 04:03:14 BACKUP kernel: [199116.268755] ata5: hard resetting link
Mar  8 04:03:18 BACKUP kernel: [199120.068867] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 04:03:18 BACKUP kernel: [199120.076745] ata5.00: configured for UDMA/133
Mar  8 04:03:18 BACKUP kernel: [199120.076748] ata5: EH complete
Mar  8 04:17:08 BACKUP kernel: [199950.056384] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 04:17:08 BACKUP kernel: [199950.059687] ata5: irq_stat 0x00400040, connection status changed
Mar  8 04:17:08 BACKUP kernel: [199950.062990] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 04:17:08 BACKUP kernel: [199950.066275] ata5: hard resetting link
Mar  8 04:17:12 BACKUP kernel: [199953.868129] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 04:17:12 BACKUP kernel: [199953.876477] ata5.00: configured for UDMA/133
Mar  8 04:17:12 BACKUP kernel: [199953.876487] ata5: EH complete
Mar  8 04:31:00 BACKUP kernel: [200781.866959] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 04:31:00 BACKUP kernel: [200781.867798] ata5: irq_stat 0x00400040, connection status changed
Mar  8 04:31:00 BACKUP kernel: [200781.868598] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 04:31:00 BACKUP kernel: [200781.869328] ata5: hard resetting link
Mar  8 04:31:04 BACKUP kernel: [200785.671287] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 04:31:04 BACKUP kernel: [200785.679106] ata5.00: configured for UDMA/133
Mar  8 04:31:04 BACKUP kernel: [200785.679109] ata5: EH complete
Mar  8 05:12:18 BACKUP kernel: [203260.301564] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 05:12:18 BACKUP kernel: [203260.304875] ata5: irq_stat 0x00400040, connection status changed
Mar  8 05:12:18 BACKUP kernel: [203260.308187] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 05:12:18 BACKUP kernel: [203260.311477] ata5: hard resetting link
Mar  8 05:12:22 BACKUP kernel: [203264.112978] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 05:12:22 BACKUP kernel: [203264.121313] ata5.00: configured for UDMA/133
Mar  8 05:12:22 BACKUP kernel: [203264.121323] ata5: EH complete
Mar  8 05:17:12 BACKUP kernel: [203554.464379] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 05:17:12 BACKUP kernel: [203554.465220] ata5: irq_stat 0x00400040, connection status changed
Mar  8 05:17:12 BACKUP kernel: [203554.466044] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 05:17:12 BACKUP kernel: [203554.466865] ata5: hard resetting link
Mar  8 05:17:16 BACKUP kernel: [203558.268693] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 05:17:16 BACKUP kernel: [203558.276877] ata5.00: configured for UDMA/133
Mar  8 05:17:16 BACKUP kernel: [203558.276888] ata5: EH complete
Mar  8 12:50:20 BACKUP kernel: [230742.181061] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 12:50:20 BACKUP kernel: [230742.184389] ata5: irq_stat 0x00400040, connection status changed
Mar  8 12:50:20 BACKUP kernel: [230742.187684] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 12:50:20 BACKUP kernel: [230742.190967] ata5: hard resetting link
Mar  8 12:50:24 BACKUP kernel: [230745.994738] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 12:50:24 BACKUP kernel: [230746.002974] ata5.00: configured for UDMA/133
Mar  8 12:50:24 BACKUP kernel: [230746.002984] ata5: EH complete
Mar  8 13:19:27 BACKUP kernel: [232488.894582] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  8 13:19:27 BACKUP kernel: [232488.897921] ata5: irq_stat 0x00400040, connection status changed
Mar  8 13:19:27 BACKUP kernel: [232488.901223] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  8 13:19:27 BACKUP kernel: [232488.904512] ata5: hard resetting link
Mar  8 13:19:31 BACKUP kernel: [232492.705097] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 13:19:31 BACKUP kernel: [232492.713409] ata5.00: configured for UDMA/133
Mar  8 13:19:31 BACKUP kernel: [232492.713419] ata5: EH complete
Mar  8 13:50:06 BACKUP kernel: [234327.682923] ata5: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
Mar  8 13:50:06 BACKUP kernel: [234327.686253] ata5: irq_stat 0x00400040, connection status changed
Mar  8 13:50:06 BACKUP kernel: [234327.689554] ata5: SError: { HostInt PHYRdyChg 10B8B DevExch }
Mar  8 13:50:06 BACKUP kernel: [234327.692850] ata5: hard resetting link
Mar  8 13:50:09 BACKUP kernel: [234331.495345] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 13:50:09 BACKUP kernel: [234331.503681] ata5.00: configured for UDMA/133
Mar  8 13:50:09 BACKUP kernel: [234331.503691] ata5: EH complete
Mar  8 19:30:50 BACKUP kernel: [254772.468164] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
Mar  8 19:30:50 BACKUP kernel: [254772.471476] ata5: irq_stat 0x00400040, connection status changed
Mar  8 19:30:50 BACKUP kernel: [254772.474792] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  8 19:30:50 BACKUP kernel: [254772.478083] ata5: hard resetting link
Mar  8 19:30:55 BACKUP kernel: [254776.895846] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  8 19:30:55 BACKUP kernel: [254776.904167] ata5.00: configured for UDMA/133 [COLOR=#393939]Mar  8 19:30:55 BACKUP kernel: [254776.904177] ata5: EH complete[/COLOR]
```


From what I've been able to read, people are pointing to a bad sata cable. Some of the drives in the stripe sets have errors, but nothing critical as some of these drives have 35000 hours on them, and the errors I'm referring to happened thousands of hours ago.

So;

1. how can I start to track down this error
and 
2. how can I determine what drive ata5 is?

Interestingly enough the command:
```
root@BACKUP:/# lshw -businfo -C disk
```

produces this

```
Bus info          Device     Class          Description
=======================================================
scsi@0:0.0.0      /dev/sda   disk           320GB WDC WD3200KS-00P
scsi@1:0.0.0      /dev/sdb   disk           320GB WDC WD3200KS-00P
scsi@2:0.0.0      /dev/sdc   disk           160GB Maxtor 6V160E0
scsi@3:0.0.0      /dev/sdd   disk           160GB Maxtor 6V160E0
scsi@4:0.0.0      /dev/sde   disk           37GB WDC WD360GD-00FL
scsi@6:0.0.0      /dev/sdf   disk           200GB ST3200826AS
scsi@7:0.0.0      /dev/sdg   disk           200GB ST3200826AS
scsi@8:0.0.0      /dev/sdh   disk           200GB ST3200826AS
scsi@9:0.0.0      /dev/sdi   disk           200GB ST3200826AS
scsi@10:0.0.0     /dev/sdj   disk           37GB WDC WD360GD-00FL
scsi@11:0.0.0     /dev/sdk   disk           37GB WDC WD360GD-00FL
```


no drive 5. /dev/sde is the os drive


And here is the kern.log upon reboot

```
[COLOR=#393939]Mar  9 22:38:45 BACKUP kernel: [   12.784096] ata5.00: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen[/COLOR]Mar  9 22:38:45 BACKUP kernel: [   12.784130] ata5.00: irq_stat 0x00400040, connection status changed
Mar  9 22:38:45 BACKUP kernel: [   12.784146] ata5: SError: { PHYRdyChg 10B8B DevExch }
Mar  9 22:38:45 BACKUP kernel: [   12.784171] ata5.00: failed command: READ DMA
Mar  9 22:38:45 BACKUP kernel: [   12.784185] ata5.00: cmd c8/00:08:f0:7b:4d/00:00:00:00:00/e4 tag 0 dma 4096 in
Mar  9 22:38:45 BACKUP kernel: [   12.784185]          res 50/00:00:37:b0:9d/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Mar  9 22:38:45 BACKUP kernel: [   12.784240] ata5.00: status: { DRDY }
Mar  9 22:38:45 BACKUP kernel: [   12.784254] ata5: hard resetting link
```
Ive tried copying gigs and gigs of data to each of the arrays to try and get the error to reappear to at least tell me what array it is, no luck.

Any help would be appreciated guys!

Thanks alot. 

Jay

---

