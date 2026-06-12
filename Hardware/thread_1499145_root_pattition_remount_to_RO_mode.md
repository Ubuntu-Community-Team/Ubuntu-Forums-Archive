---
title: "root pattition remount to RO mode"
date: 2010-06-01
forum: Hardware
---

### Post by mayhem_ on 2010-06-01
hi, all

After update to 10.04 my system begins to work unstable. After some time of work root partition remount to read-only mode. When I made full reinstall of Kubuntu, problem doesn't desappear

My dmesg:

```
[ 6722.040142] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x2 action 0x6 frozen
[ 6722.040158] ata1: SError: { RecovComm }
[ 6722.040166] ata1.00: failed command: FLUSH CACHE EXT
[ 6722.040185] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 6722.040188]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[ 6722.040197] ata1.00: status: { DRDY }
[ 6722.040210] ata1: hard resetting link
[ 6722.570136] ata1: softreset failed (device not ready)
[ 6722.570149] ata1: applying SB600 PMP SRST workaround and retrying
[ 6722.750110] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 6722.751858] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 6722.753993] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 6722.754001] ata1.00: configured for UDMA/133
[ 6722.754013] ata1.00: device reported invalid CHS sector 0
[ 6722.754034] end_request: I/O error, dev sda, sector 90879152
[ 6722.754078] ata1: EH complete
[ 6722.754089] Aborting journal on device sda5-8.
[ 6722.768425] EXT4-fs error (device sda5): ext4_journal_start_sb: Detected aborted journal
[ 6722.768444] EXT4-fs (sda5): Remounting filesystem read-only
[ 6722.771630] journal commit I/O error
```i found link [https://ata.wiki.kernel.org/index.php/Libata_error_messages#SATA_SError_expansion](https://ata.wiki.kernel.org/index.php/Libata_error_messages#SATA_SError_expansion)

line ```
[ 6722.040188]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask  0x4 (**timeout**)
``` show me that error class is TIMEOUT, which means that
```
Controller failed to respond to an active ATA command.  This could be  any number of causes.  Most often this is due to an unrelated interrupt  subsystem bug (try booting with 'pci=nomsi' or 'acpi=off' or 'noapic'),  which failed to deliver an interrupt when we were expecting one from the  hardware. 
```But when I made this, there were no effect.

Have someone the same error? My hard drive is half a year old.

Kernel:
Linux sheffield 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

