---
title: "sata errors in log"
date: 2010-11-10
forum: Hardware
---

### Post by roberto.tomas on 2010-11-10
unless I switch to the fullscreen console (where these messages splash into the terminal) or I am looking in my dmesg, I never notice this, but ...

I keep seeing errors like these:

```
[78652.676334] ata6: exception Emask 0x10 SAct 0x0 SErr 0x180000 action 0x6 frozen
[78652.676344] ata6: edma_err_cause=00000020 pp_flags=00000000, SError=00180000
[78652.676360] ata7: exception Emask 0x10 SAct 0x0 SErr 0x180000 action 0x6 frozen
[78652.676367] ata7: edma_err_cause=00000020 pp_flags=00000000, SError=00180000
[78652.676376] ata7: SError: { 10B8B Dispar }
[78652.676384] ata6: SError: { 10B8B Dispar }
[78652.676391] ata7: hard resetting link
[78652.676399] ata6: hard resetting link
```

hundreds of them every day, for months now. The drives themselves apear to work just fine, and I have used the ubuntu test suite and the gpartd to test and verify the disks. It doesnt appear to be them. Any ideas what software changes could cause this? at first, when I installed 10.04, (back around april) it worked without these errors. I feel pretty sure the problem is in software, but if anyone thinks it is really necessary I can boot up in the 10.04 live cd and let it sit there for a few hours and see if I get the errors.

---

### Post by roberto.tomas on 2010-11-12
bump

---

### Post by roberto.tomas on 2010-11-15
bump
 --no one know how to diagnose sata bus/hard disc linux errors?

---

### Post by roberto.tomas on 2010-11-18
bump

---

### Post by psychok9 on 2010-12-10
Same problem here with Ubuntu 10.04 and 10.10. Flawless with Ubuntu 9.10 and Windows 7.
Now, I'll test kernel 2.6.37-rc2 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).
P5Q Deluxe, Intel Q6600, Radeon 5850, 4GB DDR2 1066MHz.
The errors on 2xSeagate 160GB SATA1/NCQ assembled in Raid 0/Stripe.

```
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984016] ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984020] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984023] ata4.00: cmd 61/08:00:88:b1:e2/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984024]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984026] ata4.00: status: { DRDY }
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984028] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984031] ata4.00: cmd 61/08:08:68:d9:cb/00:00:01:00:00/40 tag 1 ncq 4096 out
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984032]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984033] ata4.00: status: { DRDY }
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  397.984036] ata4: hard resetting link
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  398.476038] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  398.478862] ata4.00: configured for UDMA/133
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  398.478867] ata4.00: device reported invalid CHS sector 0
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  398.478869] ata4.00: device reported invalid CHS sector 0
Dec 10 16:19:15 Q6600-Ubuntu kernel: [  398.478877] ata4: EH complete
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.004015] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.004019] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.004023] ata4.00: cmd 61/08:00:28:4a:e3/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.004024]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.004025] ata4.00: status: { DRDY }
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.004029] ata4: hard resetting link
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.496009] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.498908] ata4.00: configured for UDMA/133
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.498911] ata4.00: device reported invalid CHS sector 0
Dec 10 16:20:18 Q6600-Ubuntu kernel: [  461.498918] ata4: EH complete
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976019] ata4.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x6 frozen
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976023] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976027] ata4.00: cmd 61/08:00:a8:6b:e3/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976028]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976030] ata4.00: status: { DRDY }
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976032] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976035] ata4.00: cmd 61/08:08:d0:cb:0b/00:00:08:00:00/40 tag 1 ncq 4096 out
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976036]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976038] ata4.00: status: { DRDY }
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976039] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976043] ata4.00: cmd 61/08:10:68:e2:0b/00:00:08:00:00/40 tag 2 ncq 4096 out
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976043]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976045] ata4.00: status: { DRDY }
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976046] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976050] ata4.00: cmd 61/10:18:70:e2:0b/00:00:08:00:00/40 tag 3 ncq 8192 out
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976051]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976052] ata4.00: status: { DRDY }
Dec 10 16:21:15 Q6600-Ubuntu kernel: [  518.976055] ata4: hard resetting link
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.469508] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.472376] ata4.00: configured for UDMA/133
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.472380] ata4.00: device reported invalid CHS sector 0
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.472382] ata4.00: device reported invalid CHS sector 0
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.472383] ata4.00: device reported invalid CHS sector 0
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.472385] ata4.00: device reported invalid CHS sector 0
Dec 10 16:21:16 Q6600-Ubuntu kernel: [  519.472393] ata4: EH complete
Dec 10 16:21:45 Q6600-Ubuntu kernel: [  548.100007] usb 2-6: new high speed USB device using ehci_hcd and address 3
Dec 10 16:21:45 Q6600-Ubuntu kernel: [  548.232742] hub 2-6:1.0: USB hub found
Dec 10 16:21:45 Q6600-Ubuntu kernel: [  548.232852] hub 2-6:1.0: 4 ports detected
Dec 10 16:21:47 Q6600-Ubuntu kernel: [  550.964015] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Dec 10 16:21:47 Q6600-Ubuntu kernel: [  550.964018] ata3.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:21:47 Q6600-Ubuntu kernel: [  550.964022] ata3.00: cmd 61/08:00:08:6f:e3/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:21:47 Q6600-Ubuntu kernel: [  550.964023]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:21:47 Q6600-Ubuntu kernel: [  550.964025] ata3.00: status: { DRDY }
Dec 10 16:21:47 Q6600-Ubuntu kernel: [  550.964028] ata3: hard resetting link
Dec 10 16:21:48 Q6600-Ubuntu kernel: [  551.456008] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:21:48 Q6600-Ubuntu kernel: [  551.458850] ata3.00: configured for UDMA/133
Dec 10 16:21:48 Q6600-Ubuntu kernel: [  551.458853] ata3.00: device reported invalid CHS sector 0
Dec 10 16:21:48 Q6600-Ubuntu kernel: [  551.458859] ata3: EH complete
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  608.992013] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  608.992017] ata3.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  608.992021] ata3.00: cmd 61/08:00:d8:08:e2/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  608.992022]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  608.992024] ata3.00: status: { DRDY }
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  608.992027] ata3: hard resetting link
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  609.485015] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  609.487820] ata3.00: configured for UDMA/133
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  609.487824] ata3.00: device reported invalid CHS sector 0
Dec 10 16:22:46 Q6600-Ubuntu kernel: [  609.487832] ata3: EH complete
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992012] ata4.00: NCQ disabled due to excessive errors
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992015] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992019] ata4.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992023] ata4.00: cmd 61/08:00:90:d9:e2/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992023]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992025] ata4.00: status: { DRDY }
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  680.992028] ata4: hard resetting link
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  681.484010] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  681.486862] ata4.00: configured for UDMA/133
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  681.486866] ata4.00: device reported invalid CHS sector 0
Dec 10 16:23:58 Q6600-Ubuntu kernel: [  681.486874] ata4: EH complete
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.056010] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.056014] ata3.00: failed command: WRITE FPDMA QUEUED
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.056018] ata3.00: cmd 61/08:00:f8:d6:e3/00:00:00:00:00/40 tag 0 ncq 4096 out
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.056018]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.056020] ata3.00: status: { DRDY }
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.056023] ata3: hard resetting link
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.548009] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.551055] ata3.00: configured for UDMA/133
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.551059] ata3.00: device reported invalid CHS sector 0
Dec 10 16:26:30 Q6600-Ubuntu kernel: [  833.551067] ata3: EH complete
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1262.992014] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1262.992017] ata3.00: failed command: FLUSH CACHE EXT
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1262.992021] ata3.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1262.992022]          res 40/00:00:00:4f:c2/00:00:00:4f:c2/00 Emask 0x4 (timeout)
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1262.992024] ata3.00: status: { DRDY }
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1262.992027] ata3: hard resetting link
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1263.484009] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1263.486770] ata3.00: configured for UDMA/133
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1263.486772] ata3.00: retrying FLUSH 0xea Emask 0x4
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1263.486797] ata3.00: device reported invalid CHS sector 0
Dec 10 16:33:40 Q6600-Ubuntu kernel: [ 1263.486802] ata3: EH complete
```

---

