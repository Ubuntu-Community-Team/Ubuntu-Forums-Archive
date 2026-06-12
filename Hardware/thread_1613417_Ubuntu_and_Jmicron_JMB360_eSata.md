---
title: "Ubuntu and Jmicron JMB360 eSata"
date: 2010-11-04
forum: Hardware
---

### Post by Jgru on 2010-11-04
Hi there,

I've been fiddling with ubuntu for a while now and im liking it. With a  newly bought SSD it just feels a lot snappier than W7. There is one  thing, however, that keeps me from being totally converted.

First, some specs:
I run the latest 10.10 with 2.6.35.22 kernel, 64 bit version(so updating  from Lynx didn't fix it). Hardware consists of Asus G1Sn laptop, OCZ  Vertex 2 -SSD and an external eSata/USB hard disk for storage.

Now, the problem is the JMicron JMB360 eSata/SCSI controller. I've tried searching for solutions literally for days, but no-one seems to have exactly the problems im having (though a lot eSata -related problems are out there).
The problem is, that when the HDD is hooked up with eSata, it initially recognizes the drive fine and it shows up in Disk Utility etc. However, any attempts to access/mounting it fails with a timeout. The drive simply disappears.
I realize that linux and windows handle things very differently, but initially in windows i had the same problem (with the exception that the timing out caused all external ports of the laptop to fail). This, however, was fixed by JMicron by a newer driver so I know the drive and the controller are completely cabable of doing their thing.

So, back to ubuntu. There seems to be no such "updated driver" and contacts to jmicron have gone unanswered. I have gone through their site for updates and it seems that the drivers for the controller are in the kernel ([ftp://driver.jmicron.com.tw/jmb36x/](ftp://driver.jmicron.com.tw/jmb36x/) have some updates to other linux distros).
Nothing eSata-related (jmicron especially) are mentioned in the newer kernel changelogs.

I turn to you, the community, through which all linux-related is powered. I expect getting some general remarks about the search function, but im going to plunge straight into the flames.
All the commands through the terminal that i've found have been of no use.

Here's my system log after unplugging the usb and connecting the esata cable.

```
Nov  4 18:05:19 ubuntu kernel: [ 3646.307048] usb 2-3: USB disconnect, address 3
Nov  4 18:05:21 ubuntu kernel: [ 3649.011957] ata6: hard resetting link
Nov  4 18:05:26 ubuntu kernel: [ 3653.780192] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov  4 18:05:26 ubuntu kernel: [ 3653.792432] ata6.00: ATA-6: SAMSUNG HD103SI, 1AG01118, max UDMA/133
Nov  4 18:05:26 ubuntu kernel: [ 3653.792438] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Nov  4 18:05:26 ubuntu kernel: [ 3653.805948] ata6.00: configured for UDMA/133
Nov  4 18:05:26 ubuntu kernel: [ 3653.805960] ata6: EH complete
Nov  4 18:05:26 ubuntu kernel: [ 3653.806154] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
Nov  4 18:05:26 ubuntu kernel: [ 3653.806422] sd 5:0:0:0: Attached scsi generic sg2 type 0
Nov  4 18:05:26 ubuntu kernel: [ 3653.806598] sd 5:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Nov  4 18:05:26 ubuntu kernel: [ 3653.806688] sd 5:0:0:0: [sdb] Write Protect is off
Nov  4 18:05:26 ubuntu kernel: [ 3653.806734] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  4 18:05:26 ubuntu kernel: [ 3653.807874]  sdb: sdb1
Nov  4 18:05:26 ubuntu kernel: [ 3653.812106] sd 5:0:0:0: [sdb] Attached SCSI disk
Nov  4 18:05:26 ubuntu kernel: [ 3653.991933] ata6: hard resetting link
Nov  4 18:05:27 ubuntu kernel: [ 3654.340057] ata6: SATA link down (SStatus 0 SControl 300)
Nov  4 18:05:27 ubuntu kernel: [ 3654.503665] ata6: hard resetting link
Nov  4 18:05:37 ubuntu kernel: [ 3664.510160] ata6: hard resetting link
Nov  4 18:05:41 ubuntu kernel: [ 3669.277863] usb 2-2.3: USB disconnect, address 7
Nov  4 18:05:47 ubuntu kernel: [ 3674.540059] ata6: hard resetting link
Nov  4 18:05:57 ubuntu kernel: [ 3685.160039] ata6: link is slow to respond, please be patient (ready=0)
Nov  4 18:06:22 ubuntu kernel: [ 3709.600102] ata6: limiting SATA link speed to 1.5 Gbps
Nov  4 18:06:22 ubuntu kernel: [ 3709.600107] ata6: hard resetting link
Nov  4 18:06:27 ubuntu kernel: [ 3714.832695] ata6.00: disabled
Nov  4 18:06:27 ubuntu kernel: [ 3714.832734] ata6: hard resetting link
Nov  4 18:06:37 ubuntu kernel: [ 3724.880123] ata6: hard resetting link
Nov  4 18:06:47 ubuntu kernel: [ 3734.930110] ata6: hard resetting link
Nov  4 18:06:58 ubuntu kernel: [ 3745.952681] ata6: link is slow to respond, please be patient (ready=0)
Nov  4 18:07:22 ubuntu kernel: [ 3769.982551] ata6: limiting SATA link speed to 1.5 Gbps
Nov  4 18:07:22 ubuntu kernel: [ 3769.982556] ata6: hard resetting link
Nov  4 18:07:27 ubuntu kernel: [ 3775.192605] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  4 18:07:27 ubuntu kernel: [ 3775.192611] sd 5:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Nov  4 18:07:27 ubuntu kernel: [ 3775.192619] Descriptor sense data with sense descriptors (in hex):
Nov  4 18:07:27 ubuntu kernel: [ 3775.192623]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov  4 18:07:27 ubuntu kernel: [ 3775.192639]         00 00 00 b7 
Nov  4 18:07:27 ubuntu kernel: [ 3775.192646] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
Nov  4 18:07:27 ubuntu kernel: [ 3775.192653] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 b7 00 00 08 00
Nov  4 18:07:27 ubuntu kernel: [ 3775.192673] quiet_error: 12 callbacks suppressed
Nov  4 18:07:27 ubuntu kernel: [ 3775.192718] ata6: EH complete
Nov  4 18:07:27 ubuntu kernel: [ 3775.192776] ata6.00: detaching (SCSI 5:0:0:0)
Nov  4 18:07:27 ubuntu kernel: [ 3775.220292] sd 5:0:0:0: [sdb] Synchronizing SCSI cache
Nov  4 18:07:27 ubuntu kernel: [ 3775.220359] sd 5:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Nov  4 18:07:27 ubuntu kernel: [ 3775.220367] sd 5:0:0:0: [sdb] Stopping disk
Nov  4 18:07:27 ubuntu kernel: [ 3775.220837] sd 5:0:0:0: [sdb] START_STOP FAILED
Nov  4 18:07:27 ubuntu kernel: [ 3775.220842] sd 5:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
```The bug-discussion at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871) pretty much says the same thing, but a bit different errors. All that thread gives me though is that no-one has found a solution.

Thank you.

---

