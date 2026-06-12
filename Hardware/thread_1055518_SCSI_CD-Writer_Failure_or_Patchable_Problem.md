---
title: "SCSI CD-Writer Failure or Patchable Problem?"
date: 2009-01-30
forum: Hardware
---

### Post by admarshall on 2009-01-30
I'm trying to maintain an ancient box for a non-profit using Hardy Heron (8.04).  It's got an hp cd-writer 9100 series for which no setup CDs are available, but Ubuntu got going.  

Unfortunately, its now giving "Unsafe Removal" messages under Win2K (dual boot) and causing annoyingly excessive boot-up times under Ubuntu. While booting, the screen flips out of GUI mode into console for a while and the following messages appear, repeatedly. The context of those messages is provided after them. (All extracts below were recorded in /var/log/messages and copied from the current working session to here).

I'm just wondering if anyone might know whether or not this is a case of the CD-writer dying, without cost-feasible hope of repair, or if i might be able to do something simple and cheap to fix this, with, say, a patch or twiddling some cables or whatever.  

My undying gratitude in advance for any suggestions or just THANX!

===== Extract from /var/log/messages referred to above ================
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380038] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380056] ata2.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380058]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380060]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380064] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [   67.416403] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan 30 16:22:33 tdmdq-mt1 kernel: [   72.396844] ata2: device not ready (errno=-16), forcing hardreset
Jan 30 16:22:33 tdmdq-mt1 kernel: [   72.396848] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [   73.044580] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   73.208564] ata2.01: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   73.208582] ata2: EH complete

========== Apparently relevant context from /var/log/messages =======
[[Prior lines of /var/log/messages cut; Complete file in tarball attached]]
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.064159] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.064164] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.226954] ata1.00: ATA-5: MAXTOR 6L040J2, A93.0500, max UDMA/133
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.226960] ata1.00: 78177792 sectors, multi 16: LBA
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.242678] ata1.00: configured for UDMA/133
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.886146] ata2.00: ATAPI: Hewlett-Packard CD-Writer Plus 9100, 1.0c, max UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   31.886169] ata2.01: ATAPI: LTN526D, YSR5, max UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.057890] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.221877] ata2.01: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.222065] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L040J2   A93. PQ: 0 ANSI: 5
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.227023] scsi 1:0:0:0: CD-ROM            HP       CD-Writer+ 9100  1.0c PQ: 0 ANSI: 5
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.227675] scsi 1:0:1:0: CD-ROM            LITEON   CD-ROM LTN526D   YSR5 PQ: 0 ANSI: 5
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.246956] Driver 'sd' needs updating - please use bus_type methods
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247092] sd 0:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247111] sd 0:0:0:0: [sda] Write Protect is off
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247114] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247136] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247201] sd 0:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247213] sd 0:0:0:0: [sda] Write Protect is off
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247216] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247235] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.247240]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.261642]  sda1 sda2 sda3 < sda5 >
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.284746] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.291727] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.291761] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.291783] scsi 1:0:1:0: Attached scsi generic sg2 type 5
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.340864] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.340873] Uniform CD-ROM driver Revision: 3.20
Jan 30 16:22:33 tdmdq-mt1 kernel: [   32.340954] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380038] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380056] ata2.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380058]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380060]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [   62.380064] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [   67.416403] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan 30 16:22:33 tdmdq-mt1 kernel: [   72.396844] ata2: device not ready (errno=-16), forcing hardreset
Jan 30 16:22:33 tdmdq-mt1 kernel: [   72.396848] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [   73.044580] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   73.208564] ata2.01: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [   73.208582] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  103.186835] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  103.186844] ata2.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
Jan 30 16:22:33 tdmdq-mt1 kernel: [  103.186846]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  103.186848]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  103.186851] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  108.223224] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  113.203664] ata2: device not ready (errno=-16), forcing hardreset
Jan 30 16:22:33 tdmdq-mt1 kernel: [  113.203667] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  113.851399] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  114.015384] ata2.01: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  114.015390] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  143.993656] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  143.993666] ata2.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
Jan 30 16:22:33 tdmdq-mt1 kernel: [  143.993667]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  143.993669]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  143.993672] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  149.030043] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  154.010483] ata2: device not ready (errno=-16), forcing hardreset
Jan 30 16:22:33 tdmdq-mt1 kernel: [  154.010486] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  154.658220] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  154.822206] ata2.01: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  154.822212] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  184.800477] ata2.01: limiting speed to UDMA/25:PIO4
Jan 30 16:22:33 tdmdq-mt1 kernel: [  184.800481] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  184.800490] ata2.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
Jan 30 16:22:33 tdmdq-mt1 kernel: [  184.800491]          cdb 5a 00 2a 00 00 00 00 00  80 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  184.800493]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  184.800497] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  189.836864] ata2: port is slow to respond, please be patient (Status 0xd0)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  194.817304] ata2: device not ready (errno=-16), forcing hardreset
Jan 30 16:22:33 tdmdq-mt1 kernel: [  194.817307] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  196.671233] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x3)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  196.671237] ata2.00: revalidation failed (errno=-5)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  196.671240] ata2: failed to recover some devices, retrying in 5 secs
Jan 30 16:22:33 tdmdq-mt1 kernel: [  205.865402] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  207.407566] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x3)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  207.407569] ata2.00: revalidation failed (errno=-5)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  207.407572] ata2: failed to recover some devices, retrying in 5 secs
Jan 30 16:22:33 tdmdq-mt1 kernel: [  209.970397] usplash[1234]: segfault at b77cd3c0 eip b7f6ef19 esp bfbba290 error 6
Jan 30 16:22:33 tdmdq-mt1 kernel: [  212.404756] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  213.220345] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  213.384328] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  213.384367] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  213.384385] sr1: scsi-1 drive
Jan 30 16:22:33 tdmdq-mt1 kernel: [  213.384471] sr 1:0:1:0: Attached scsi CD-ROM sr1
Jan 30 16:22:33 tdmdq-mt1 kernel: [  244.361885] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  244.362415] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan 30 16:22:33 tdmdq-mt1 kernel: [  244.362417]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  244.362418]          res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  244.362866] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  244.363156] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  245.177492] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  245.341484] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  245.341492] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.319747] ata2.01: qc timeout (cmd 0xa0)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.319753] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.320268] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.320269]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.320271]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.320717] ata2.01: status: { DRDY ERR }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  275.321020] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  276.135354] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  276.299339] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  276.299348] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  306.277607] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  306.278122] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan 30 16:22:33 tdmdq-mt1 kernel: [  306.278124]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  306.278126]          res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  306.278572] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  306.278850] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  307.093218] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  307.257201] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  307.257207] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  337.235472] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  337.235987] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan 30 16:22:33 tdmdq-mt1 kernel: [  337.235989]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  337.235990]          res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  337.236437] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  337.236715] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  338.051080] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  338.215064] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  338.215071] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  343.211197] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  343.211712] ata2.01: cmd a0/00:00:00:fe:00/00:00:00:00:00/b0 tag 0 pio 254 in
Jan 30 16:22:33 tdmdq-mt1 kernel: [  343.211714]          cdb 12 01 00 00 fe 00 00 00  00 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  343.211716]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  343.212230] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  343.212508] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  344.026807] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  344.190791] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  344.190800] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.183352] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.183866] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.183868]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.183870]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.184316] ata2.01: status: { DRDY }
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.184594] ata2: soft resetting link
Jan 30 16:22:33 tdmdq-mt1 kernel: [  354.998962] ata2.00: configured for UDMA/33
Jan 30 16:22:33 tdmdq-mt1 kernel: [  355.162945] ata2.01: configured for UDMA/25
Jan 30 16:22:33 tdmdq-mt1 kernel: [  355.162950] ata2: EH complete
Jan 30 16:22:33 tdmdq-mt1 kernel: [  355.298094] Attempting manual resume
Jan 30 16:22:33 tdmdq-mt1 kernel: [  355.298100] swsusp: Resume From Partition 8:5
[[cut]]

---

### Post by nixscripter on 2009-01-31
The "unsafe removal" I think is a bad sign, but I'm not good at debugging SCSI problems. I have a different suggestion.

When the computer does eventually boot into Ubuntu, install the cdrecord package if you don't have it (from Synaptic package manager), and then in a Terminal, type: ```
cdrecord -scanbus
```

Does the device appear in the output?

---

### Post by admarshall on 2009-01-31
> **nixscripter said:**
> The "unsafe removal" I think is a bad sign, but I'm not good at debugging SCSI problems. I have a different suggestion.

When the computer does eventually boot into Ubuntu, install the cdrecord package if you don't have it (from Synaptic package manager), and then in a Terminal, type: ```
cdrecord -scanbus
```

Does the device appear in the output?

I'm not sure.  Here's the output before and after inserting a (possibly very OLD, supposedly blank) Ricoh Type 74 650MB CD-R:
```
mt1@tdmdq-mt1:~$ cdrecord -scanbus
scsibus1:
	1,0,0	100) *
	1,1,0	101) '@&#65533;L&#65533;' '' '\&#65533;&#65533;' Disk
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
mt1@tdmdq-mt1:~$ cdrecord -scanbus
scsibus1:
	1,0,0	100) *
wodim: Warning: controller returns wrong size for CD capabilities page.
	1,1,0	101) 'LITEON  ' 'CD-ROM LTN526D  ' '&#65533;SR5' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
mt1@tdmdq-mt1:~$ 

```

---

### Post by admarshall on 2009-01-31
Notably, the eject button on the HP CD-Writer drive wouldn't work after the (supposedly) blank disk was inserted, and, the disk didn't show up in Nautilus or as a desktop icon.

I'll try checking cable connections, later, but will still be grateful for any suggestions.

---

### Post by nixscripter on 2009-01-31
That's really odd. It's definitely a hardware problem.

I would hope that it's the cables, because the drive does indicate it can register properly, so all is not probably lost. Another test you can do: copy a CD to an ISO on disk, preferably one that's pretty full. Insert it, and use this command: ```
readcd f=mycopy.iso dev=1,1,0
```

If it has problems detecting the drive, try it more than once. See if you can get through all of the data, and how often it would have to retry.

---

### Post by admarshall on 2009-02-04
SOLVED

After this box could not longer get past the BIOS' "Checking for IDE drives..." message on boot-up, i finally cracked open up the case (something i am generally loathe to do, not being a hardware type :)). 

I then unplugged the HP CD-Writer's cable to the mainboard's controller socket, at the cd-drive end, and powered up again.  The box booted-up OK, suggesting the cd-drive or it's connection was indeed causing the slow and failed boot-up problems and attendant error messages.  

Knowing this box had been sitting for several months, if not years, unused and unmaintained, before i revived it with Ubuntu, i suspected connector-corrosion from dust or humidity (an all-too-common problem back in the more humid and dusty Saigon). So, i wriggled and unplugged and replugged the cd-drive's data-cable connections at the mainboard SCSI drive-controller socket and on the drive, then booted up again.  

All problems cited above disappeared, including the error messages listed at the beginning of this thread.  The drive now reads without apparent error.  I haven't tried writing to it yet. 

Sorry for an inconvenience caused by my procrastination when it comes to playing with hardware. :D :rolleyes:

---

### Post by nixscripter on 2009-02-04
Glad to hear it. Please mark this thread as solved (under the thread tools menu).

---

