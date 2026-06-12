---
title: "Load S-ATA modules earlier at boot?"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-04-09
Hi, I've got an msi mainboard, 875 chipset, with the intel ich5 southbridge (s-ata support). When I boot ubuntu hoary, it goes through the fstab, tries to mount everything, but /dev/sda* isn't there, because the needed modules hasn't been loaded yet.

```
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 18
ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 18
usb 2-2: USB disconnect, address 2
ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
ata1: dev 0 configured for UDMA/133
scsi0 : ata_piix
ata2: SATA port has no device.
scsi1 : ata_piix
  Vendor: ATA       Model: ST3160023AS       Rev: 3.18
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4
```

So, I get an error message, that my filesystem might be corrupted, and I'm adviced to check them. But they're not corrupted of course. Pressing control+d instead of typing the root password works fine, it continues to boot and later mounts /dev/sda* to their proper mountpoints.

This is very irritating, I can't boot the computer unattended as it is now. :(
I'm using 2.6.10-5-686-smp, I've tried with 2.6.11 but nope, with 2.6.11 I get errors on the hda harddrive (not the s-ata one) about buffers, something about buffers anyway, and /sbin/getty failing, and it's being delayed for 5 minutes. So that one doesn't boot. Other than this, everything is fine..

Any solutions?

---

### Post by fackamato on 2005-04-10
Rah, too advanced question for this forum? :P

---

### Post by darkaudit on 2005-04-10
I had similar issues with my Abit NF7-S v.2 board. I fixed it by making sure all the modules needed were in /etc/modules. I also moved procps.sh to S29procps.sh in /etc/rcS.d. Now everything is in place when it comes time to check the filesystem.

---

### Post by fackamato on 2005-04-10
[QUOTE=darkaudit]I had similar issues with my Abit NF7-S v.2 board. I fixed it by making sure all the modules needed were in /etc/modules. I also moved procps.sh to S29procps.sh in /etc/rcS.d. Now everything is in place when it comes time to check the filesystem.[/QUOTE]

Now I've added some modules to /etc/modules , my procps.sh was alredy S30procps.sh ... I'll try to reboot now.

Thanks!

---

