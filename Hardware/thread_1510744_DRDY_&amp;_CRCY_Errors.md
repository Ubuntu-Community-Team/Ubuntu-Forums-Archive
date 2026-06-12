---
title: "DRDY &amp; CRCY Errors"
date: 2010-06-15
forum: Hardware
---

### Post by Sutur on 2010-06-15
Hi, for months now I've been getting some very strange hard disk errors.

Sometimes when I boot my computer the screen is flooded with them and data is missing when it finally boots.

Other times I may only get 2, or no errors, and the data is all there and completely intact!

I don't know if this is hardware error or just a bug since the data is elusive and unpredictable.

This is *really* frustrating because it's pot luck as to whether I can use my computer when I turn it on.

Here is an example of these errors:

```

**dmesg**
[   15.184692] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x0
[   15.184751] ata1.01: SError: { UnrecovData Handshk }
[   15.184806] ata1.01: cmd ca/00:08:bf:00:00/00:00:00:00:00/f0 tag 0 dma 4096 out
[   15.184807]          res 51/84:01:bf:00:00/00:00:00:00:00/f0 Emask 0x30 (host bus error)
[   15.184910] ata1.01: status: { DRDY ERR }
[   15.184956] ata1.01: error: { ICRC ABRT }
[   15.185007] ata1.00: hard resetting link
[   15.504317] ata1.01: hard resetting link
[   15.980179] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   15.980193] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   16.012287] ata1.00: configured for UDMA/133
[   16.025166] ata1.01: configured for UDMA/133
[   16.025173] ata1: EH complete
[   16.206818] REISERFS (device sdb1): replayed 29 transactions in 2 seconds
[   16.226245]   alloc irq_desc for 22 on node -1
[   16.226247]   alloc kstat_irqs on node -1
[   16.226252] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.226274] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.277210] REISERFS (device sdb1): Using r5 hash to sort names
[   16.812055] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[   16.812110] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   16.891983] sky2 eth0: enabling interface
[   16.892120] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.910872] sky2 eth1: enabling interface
[   16.911003] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.266382] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x0
[   18.266441] ata1.01: SError: { UnrecovData Handshk }
[   18.266496] ata1.01: cmd ca/00:08:0f:9c:00/00:00:00:00:00/f0 tag 0 dma 4096 out
[   18.266497]          res 51/84:01:0f:9c:00/00:00:00:00:00/f0 Emask 0x30 (host bus error)
[   18.266600] ata1.01: status: { DRDY ERR }
[   18.266646] ata1.01: error: { ICRC ABRT }
[   18.266696] ata1.00: hard resetting link
[   18.583104] ata1.01: hard resetting link
[   19.058966] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.058980] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.091078] ata1.00: configured for UDMA/133
[   19.099192] ata1.01: configured for UDMA/133
[   19.099199] ata1: EH complete
[   19.896124] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control both
[   19.896262] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   22.400918] ata1.01: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x0
[   22.401009] ata1.01: SError: { UnrecovData Handshk }
[   22.401073] ata1.01: cmd ca/00:08:bf:00:00/00:00:00:00:00/f0 tag 0 dma 4096 out
[   22.401074]          res 51/84:01:bf:00:00/00:00:00:00:00/f0 Emask 0x30 (host bus error)
[   22.401233] ata1.01: status: { DRDY ERR }
[   22.401292] ata1.01: error: { ICRC ABRT }
[   22.401356] ata1.00: hard resetting link
[   22.717233] ata1.01: hard resetting link
[   23.193095] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   23.193110] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   23.229677] ata1.00: configured for UDMA/133
[   23.249955] ata1.01: configured for UDMA/133
[   23.249963] ata1: EH complete
[   30.810029] eth1: no IPv6 routers present
```

---

### Post by Sutur on 2010-06-16
C'mon guys 51 views no answers? I know it's a new post but this has been going on for months now :(

---

### Post by Sutur on 2010-06-18
Sorry for bump, need to resolve this.

---

### Post by Sutur on 2010-06-20
bump

---

### Post by penguinfan on 2010-06-27
I had the same problem. Initially i just pressed escape to see the errors and Ctrl + Alt + del to get to the logon screen. But i had problems with mounting cd/dvd and external disks.

Eventually i just did a check and repair on the ofending disk with gparted and that solved my issue. Obviously i wasnt to worried about losing data on the disk.
Hope it helps :)

---

### Post by Sutur on 2010-07-04
Using a different kernel seems to have done the trick for the time being. I will update this thread in a month or two, if it doesn't happen then I'll mark it solved.

---

### Post by Sutur on 2010-07-06
Spoke too soon. I'm still having errors is there no-one that knows what these errors mean. I've used ubuntu gapless for four years but I'm giving serious consideration to wiping and just using Windows.

PLEASE HELP

---

### Post by pete78 on 2010-10-30
Hi, I have the same problem since many month. When it happened the first time, I could "solve" it by using an old IDE hard disk. The problem occurs only with the SATA hard disk. It is a WD5000AAKS with SATA2.
Some weeks ago, I again switched to the SATA disk and hoped, that the bug in Ubuntu (if there is one) was fixed in the meantime. I also replaced the SATA disk by a new one of the same type, but the problem persists.
Is it possible, that the problems is located on the main board? I could not exchange it for test purpose. It is a Intel motherboard DP35DPM.
Thanks for help.

The log is the following (multiple times, sometimes ever minute):
```
Oct 30 22:22:35 pete-desktop kernel: [  573.732039] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct 30 22:22:35 pete-desktop kernel: [  573.732064] ata1.00: hard resetting link
Oct 30 22:22:36 pete-desktop kernel: [  574.052011] ata1.01: hard resetting link
Oct 30 22:22:36 pete-desktop kernel: [  574.528055] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 30 22:22:36 pete-desktop kernel: [  574.528068] ata1.01: SATA link down (SStatus 0 SControl 300)
Oct 30 22:22:36 pete-desktop kernel: [  574.584145] ata1.00: configured for UDMA/100
Oct 30 22:22:36 pete-desktop kernel: [  574.632023] ata1: EH complete
```

---

### Post by Sutur on 2010-10-30
Could be the Motherboard.

I'm using an Asus p6t deluxe v2, i7 920 stock clock.

---

