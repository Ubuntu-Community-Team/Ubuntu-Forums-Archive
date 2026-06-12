---
title: "usb disk crash"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by Kropotkin on 2007-01-01
For the third time in recent months, I've had a USB disk crash. I was copying a large file to it, then suddenly the program copying the file said the file system was read only. Here is the relevant output from dmesg:
```
[...]
[18539658.416000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[18539688.660000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[18539698.904000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[18539732.164000] EXT3-fs error (device sdb1): ext3_new_block: Allocating block in system zone - blocks from 16252928, length 1
[18539732.164000] Aborting journal on device sdb1.
[18539732.220000] ext3_abort called.
[18539732.220000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[18539732.220000] Remounting filesystem read-only
[18539732.240000] attempt to access beyond end of device
[18539732.240000] sdb1: rw=0, want=34097335360, limit=160071597
[...]
```

According to fdisk:
```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel

```
As far as I can tell, the disk's partition table is completely nuked, and everything on the disk is unrecoverable.

I am baffled as to why this happens. Is this hardware failure or some obscure bug in the USB subsystem? Or something else?

I am running Dapper 6.10. FWIW, this is the dmesg output generated when the disk is attached:
```
[18544364.100000] usb 5-3: new high speed USB device using ehci_hcd and address 6
[18544364.232000] usb 5-3: configuration #1 chosen from 1 choice
[18544364.232000] scsi2 : SCSI emulation for USB Mass Storage devices
[18544364.232000] usb-storage: device found at 6
[18544364.232000] usb-storage: waiting for device to settle before scanning
[18544369.232000] usb-storage: device scan complete
[18544369.232000]   Vendor: Maxtor 6  Model: 1F2E              Rev: 1BW0
[18544369.232000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[18544369.232000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[18544369.236000] sda: Write Protect is off
[18544369.236000] sda: Mode Sense: 00 38 00 00
[18544369.236000] sda: assuming drive cache: write through
[18544369.236000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[18544369.236000] sda: Write Protect is off
[18544369.236000] sda: Mode Sense: 00 38 00 00
[18544369.236000] sda: assuming drive cache: write through
[18544369.236000]  sda: sda1
```

---

### Post by meng on 2007-01-01
Is this a flash drive or solid-state disk? The former can fail after lots of (~ 1 million) writecycles.

---

### Post by Kropotkin on 2007-01-01
It is a normal ATA harddisk.

---

### Post by Woei on 2007-01-01
> **Kropotkin said:**
> For the third time in recent months, I've had a USB disk crash. I was copying a large file to it, then suddenly the program copying the file said the file system was read only. Here is the relevant output from dmesg:
```

[18539658.416000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[18539688.660000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[18539698.904000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
[18539732.164000] EXT3-fs error (device sdb1): ext3_new_block: Allocating block in system zone - blocks from 16252928, length 1
[18539732.164000] Aborting journal on device sdb1.
[18539732.220000] ext3_abort called.
[18539732.220000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[18539732.220000] Remounting filesystem read-only
[18539732.240000] attempt to access beyond end of device
[18539732.240000] sdb1: rw=0, want=34097335360, limit=160071597

```


I've had this happen once on Warty 4.10. The cause back then could be linked to a really cheap USB2.0 hard disk enclosure with flimsy cables not designed to withstand the relatively high transfer speeds. The enclosure was a no-name, do it yourself box (i.e., you had to supply the hard disk yourself). The exact same laptop could transfer gigabytes upon gigabytes on end over a Maxtor branded enclosure without a problem whatsoever. The cable supplied with the latter was a bit thicker and I guess the chips doing the ATA <-> USB conversion were of higher quality, although that's speculation on my part.

If it's a cheap enclosure, buy something better or try higher quality USB cables. If it's an A-brand, try filing a bug report. There have been a few bug reports on kernel.org's bugzilla, like [this one](http://bugzilla.kernel.org/show_bug.cgi?id=6817) for instance. It's possible that a similar patch (inserting delays to not overwhelm the chip used) is floating around somewhere for your particular hardware.

---

