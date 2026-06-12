---
title: "Freeze &amp; HDD trouble -- can someone tell me how serious this is?"
date: 2009-08-06
forum: Hardware
---

### Post by sparklingspecks on 2009-08-06
Hello. Yesterday I tried to install something under Virtualbox (= so, the disk was in a writing-heavy phase), anyway at some point my whole desktop practically stopped responding (mouse still worked), after few minutes HDD activity lessened and somehow I got onto a different console where my computer started printing out several messages like this:

[FONT="Courier New"]
[11116.551750] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[11116.551843] ata1.00: BMDMA stat 0x25
[11116.551750] ata1.00: cmd c8/00:08:ff:94:34/00:00:00:00:00/e3 tag 0 dma 4096 in
[11116.551912]          res 51/40:00:04:95:34/00:00:00:00:00/e3 Emask 0x9 (media error)
[11116.552172] ata1.00: status: {DRDY ERROR}
[11116.552239] ata1.00: error {UNC}[/FONT]
(...)

I also had the smartctl one-minute check run ("Complete"s after 10 % "with read error"), but Gsmartcontrol tells me that "Current Pending Sector Count" & "Offline Uncorrectable" both have "1" as raw value. 
Can someone tell me, how serious this is and say if this is repairable?

---

### Post by %rm on 2009-08-23
Hi,
I keep getting almost the same *ata1.00 media error* on every boot.  The following error messages keep coming a dozen or so times, eventually it finalizes the boot and I can log in.  But also the login takes more time than usual and some applications (xterm) run slower or die altogether.  Is it about the hard disk hardware, as *media error* would suggest?  Is it possible to circumvent the problem (isolate bad parts of the media?) or will I need a new hard disk?

I ran *fsck*, answered Y to a couple of questions but nothing changed.



```

~$ dmesg
e descriptors (in hex):
[   93.870977]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   93.870985]         08 6f 22 1e 
[   93.870989] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   93.870994] end_request: I/O error, dev sda, sector 141500958
[   93.871070] ata1: EH complete
[   93.871102] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[   93.871118] sd 0:0:0:0: [sda] Write Protect is off
[   93.871120] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   93.871143] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   97.131865] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   97.131869] Bluetooth: BNEP filters: protocol multicast
[   97.152546] Bridge firewalling registered
[   99.548029] ppdev: user-space parallel port driver
[  100.779962] [drm] Initialized drm 1.1.0 20060810
[  100.787319] pci 0000:00:02.0: power state changed by ACPI to D0
[  100.787329] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  100.787336] pci 0000:00:02.0: setting latency timer to 64
[  100.787536] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  100.791461] [drm:i915_setparam] *ERROR* unknown parameter 4
[  100.791490] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  101.889290] tg3 0000:02:00.0: irq 2298 for MSI/MSI-X
[  102.115149] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  102.465641] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  103.674803] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  103.674807] tg3: eth0: Flow control is on for TX and on for RX.
[  103.675011] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

[  107.930518] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  107.930523] ata1.00: irq_stat 0x40000008
[  107.930529] ata1.00: cmd 60/08:08:6e:cf:68/00:00:08:00:00/40 tag 1 ncq 4096 in
[  107.930531]          res 41/40:00:6e:cf:68/00:00:08:00:00/40 Emask 0x409 (media error) <F>
[  107.930534] ata1.00: status: { DRDY ERR }
[  107.930536] ata1.00: error: { UNC }
[  107.956354] ata1.00: configured for UDMA/133
[  107.956366] ata1: EH complete
[  107.956418] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[  107.956437] sd 0:0:0:0: [sda] Write Protect is off
[  107.956439] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  107.956463] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by sparklingspecks on 2009-08-25
Yes, it's your hard drive. I've fixed my problem by replacing the drive (in lack of a better solution). This was relatively cheap for me, because I had a spare external drive laying around.
In case you don't want to replace the HDD straight away, you should probably prepare for it to break down soon (make (more) backups!).

---

### Post by %rm on 2009-08-26
You were right, yesterday it stopped working altogether.  Fortunately I was prepared with backups and USB stick for booting :guitar:

A friend suggested SSD for the replacement since it is silent and fast.  Do you have any experience on those ones, especially with Ubuntu?  I have a large external disk so 30-60G SSD might be enough.

---

### Post by sparklingspecks on 2009-08-29
I was interested in an SSD, too, but:
a. They're expensive, even for 8 GBs (my PC is four now, I might only keep it for another year or two, so not worth spending this much)
b. I was told SSDs generally only come with S-ATA connectors, and since your PC is probably also older than 2 years, it will most likely use ATA

On the bright side, I don't think Ubuntu will have problems with them, as they should behave like normal hard disks from the perspective of the operating system.

---

