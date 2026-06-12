---
title: "System lockups with SATA SiS182"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by ianhaycox on 2006-11-08
Hi,

Ubuntu with 2.6.15-27-k7 Kernel and SATA Sis182 controller is having frequent lockups on a second SATA hard drive when I copy large files around. I'm wondering if there is anything I can (re)-configure in the BIOS, Kernel or Controller to stop the problem.

Windows booted from the same 'problem' disk has no problems with large files, or timeouts.

Any help on a fix or diagnoses appreciated.


The following messages appear in /var/log/syslog

Nov  8 16:50:18 ian-desktop kernel: [17204859.588000] ata2: command 0x35 timeout, stat 0x58 host_stat 0x61
Nov  8 16:50:48 ian-desktop kernel: [17204889.588000] ata2: command 0x25 timeout, stat 0x58 host_stat 0x61
Nov  8 16:51:18 ian-desktop kernel: [17204919.588000] ata2: command 0x35 timeout, stat 0x58 host_stat 0x61

and the cp operation just hangs. Never waited long enough to see if the cp command completes. Usually files over about 100Mb cause the problem.

I don't think it's a hardware issue because Windows is also installed on the second drive and doesn't exhibit the problem, with no errors recorded in the error logs.

The first SATA drive functions fine.


I did temporarily upgrade the Kernel to 2.6.18 from kernel.org just to experiment and had a similar lockup problem, but the copy commands did complete eventually. Slightly different messages in syslog. E.g.

Nov  4 09:16:17 ian-desktop kernel: [ 1647.879276] ata2.00: exception Emask 0x12 SAct 0x0 SErr 0x580401 action 0x2
Nov  4 09:16:17 ian-desktop kernel: [ 1647.879283] ata2.00: (BMDMA stat 0x60)
Nov  4 09:16:17 ian-desktop kernel: [ 1647.879287] ata2.00: tag 0 cmd 0x35 Emask 0x12 stat 0x51 err 0x84 (ATA bus error)
Nov  4 09:16:17 ian-desktop kernel: [ 1648.181936] ata2: soft resetting port
Nov  4 09:16:17 ian-desktop kernel: [ 1648.332794] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  4 09:16:17 ian-desktop kernel: [ 1648.334251] ata2.00: configured for UDMA/133
Nov  4 09:16:17 ian-desktop kernel: [ 1648.334261] ata2: EH complete
Nov  4 09:16:17 ian-desktop kernel: [ 1648.341009] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Nov  4 09:16:17 ian-desktop kernel: [ 1648.341432] sdb: Write Protect is off
Nov  4 09:16:17 ian-desktop kernel: [ 1648.341435] sdb: Mode Sense: 00 3a 00 00
Nov  4 09:16:17 ian-desktop kernel: [ 1648.341751] SCSI device sdb: drive cache: write back
Nov  4 09:25:18 ian-desktop kernel: [ 2188.935719] ata2.00: exception Emask 0x12 SAct 0x0 SErr 0x580401 action 0x2 frozen
Nov  4 09:25:18 ian-desktop kernel: [ 2188.935726] ata2.00: (BMDMA stat 0x61)
Nov  4 09:25:18 ian-desktop kernel: [ 2188.935730] ata2.00: tag 0 cmd 0xca Emask 0x16 stat 0x40 err 0x0 (ATA bus error)
Nov  4 09:25:18 ian-desktop kernel: [ 2189.239082] ata2: soft resetting port
Nov  4 09:25:19 ian-desktop kernel: [ 2189.389936] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  4 09:25:19 ian-desktop kernel: [ 2189.391398] ata2.00: configured for UDMA/133
Nov  4 09:25:19 ian-desktop kernel: [ 2189.391413] ata2: EH complete
Nov  4 09:25:19 ian-desktop kernel: [ 2189.392038] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Nov  4 09:25:19 ian-desktop kernel: [ 2189.402710] sdb: Write Protect is off
Nov  4 09:25:19 ian-desktop kernel: [ 2189.402716] sdb: Mode Sense: 00 3a 00 00
Nov  4 09:25:19 ian-desktop kernel: [ 2189.403080] SCSI device sdb: drive cache: write back


Currently back to the 2.6.15.27 Kernel. Hopefully relavent messages from syslog during bootup are:

Nov  8 17:16:56 ian-desktop kernel: [17179576.404000] Uniform CD-ROM driver Revision: 3.20
Nov  8 17:16:56 ian-desktop kernel: [17179576.452000] SCSI subsystem initialized
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] ACPI: bus type scsi registered
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] libata version 1.20 loaded.
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] sata_sis 0000:00:05.0: version 0.5
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 169
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] sata_sis 0000:00:05.0: Detected SiS 182 chipset
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq
169
Nov  8 17:16:56 ian-desktop kernel: [17179576.456000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq
169
Nov  8 17:16:56 ian-desktop kernel: [17179576.672000] ata1: dev 0 cfg 00:0040 49:2f00 82:7c6b 83:7f09 84:4773 85:7c69 86:3e01 87:4763 88:407f 93:0000
Nov  8 17:16:56 ian-desktop kernel: [17179576.672000] ata1: dev 0 ATA-7, max UDMA/133, 398297088 sectors: LBA48
Nov  8 17:16:56 ian-desktop kernel: [17179576.672000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0x00000000
Nov  8 17:16:56 ian-desktop kernel: [17179576.672000] ata1: dev 0 configured for UDMA/133
Nov  8 17:16:56 ian-desktop kernel: [17179576.672000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0x00000000
Nov  8 17:16:56 ian-desktop kernel: [17179576.672000] scsi0 : sata_sis
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000] ata2: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:3c01 87:4023 88:407f 93:0000
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000] ata2: dev 0 ATA-7, max UDMA/133, 312581808 sectors: LBA48
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0x00000000
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000] ata2: dev 0 configured for UDMA/133
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0x00000000
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000] scsi1 : sata_sis
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000]   Vendor: ATA       Model: Maxtor 6V200E0    Rev: VA11
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000]   Vendor: ATA       Model: WDC WD1600JS-00M  Rev: 02.0
Nov  8 17:16:56 ian-desktop kernel: [17179576.884000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Nov  8 17:16:56 ian-desktop kernel: [17179576.892000] Driver 'sd' needs updating - please use bus_type methods
Nov  8 17:16:56 ian-desktop kernel: [17179576.896000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Nov  8 17:16:56 ian-desktop kernel: [17179576.896000] SCSI device sda: drive cache: write back
Nov  8 17:16:56 ian-desktop kernel: [17179576.900000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Nov  8 17:16:56 ian-desktop kernel: [17179576.900000] SCSI device sda: drive cache: write back
Nov  8 17:16:56 ian-desktop kernel: [17179576.900000]  sda: sda1 sda2 < sda5 >
Nov  8 17:16:56 ian-desktop kernel: [17179576.948000] sd 0:0:0:0: Attached scsi disk sda
Nov  8 17:16:56 ian-desktop kernel: [17179576.948000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Nov  8 17:16:56 ian-desktop kernel: [17179576.952000] SCSI device sdb: drive cache: write back
Nov  8 17:16:56 ian-desktop kernel: [17179576.956000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
Nov  8 17:16:56 ian-desktop kernel: [17179576.960000] SCSI device sdb: drive cache: write back
Nov  8 17:16:56 ian-desktop kernel: [17179576.960000]  sdb: sdb1 sdb2 sdb3 < sdb5 >
Nov  8 17:16:56 ian-desktop kernel: [17179577.000000] sd 1:0:0:0: Attached scsi disk sdb

Any help diagnosing the problem appreciated.

---

### Post by ianhaycox on 2006-11-10
Bump. Anyone any ideas ?

---

### Post by redactech on 2006-11-17
I don't have any idea for you,  but my desktop has a SATA drive for the big files and it start showing the same issue. It works fine for several weeks then one day it started to "timeout" (see the log below). After with trying without success to fsck it (it would take more than a night to proceed and error would remain) I decided that the HD was no good, and buy another, copy and checked the files with another desktop stuff the new HD in the desktop and mount it. I just tried to copy another big file in and it died on me and gave me the error (I,m running Dapper with 2.6.15-27-686)



> [17179637.832000] ata2: command 0x25 timeout, stat 0x50 host_stat 0x21
[17180818.720000] ata2: command 0x25 timeout, stat 0x50 host_stat 0x21
[17180818.720000] init_special_inode: bogus i_mode (0)
[17180848.720000] ata2: command 0x35 timeout, stat 0x50 host_stat 0x21
[17188892.168000] ata2: command 0x25 timeout, stat 0x50 host_stat 0x21
[17189407.864000] ata2: command 0x35 timeout, stat 0x50 host_stat 0x21
[17189439.024000] ata2: command 0x25 timeout, stat 0x50 host_stat 0x21
[17189439.024000] EXT3-fs error (device sda5): ext3_new_block: Allocating block in system zone - block = 3735552
[17189439.024000] Aborting journal on device sda5.
[17189441.088000] ext3_abort called.
[17189441.088000] EXT3-fs error (device sda5): ext3_journal_start_sb: Detected aborted journal
[17189441.088000] Remounting filesystem read-only
[17189469.024000] ata2: command 0x35 timeout, stat 0x50 host_stat 0x21
[17189469.148000] __journal_remove_journal_head: freeing b_committed_data
[17189469.148000] __journal_remove_journal_head: freeing b_committed_data
[17189469.148000] __journal_remove_journal_head: freeing b_committed_data
[17189469.148000] __journal_remove_journal_head: freeing b_committed_data
[17189469.148000] __journal_remove_journal_head: freeing b_committed_data
[17189469.148000] __journal_remove_journal_head: freeing b_committed_data

Is upgrading to the newest kernel a good idea, or should I see elsewhere ?

---

### Post by ianhaycox on 2006-11-17
Well upgrading the Kernel helped aleviate the problem. Looking at the log files on a 2.6.18 kernel it now soft resets the port after the timeout and then carries on for a while until the next timeout.

No much help, so I regressed back to the Ubuntu supported Kernel.

I am keeping an eye on kernel.org to see if there are any bug fixes. Maybe if someone else also has this problem they could post the necessary log files and I will post the whole lot as a bug report for the kernel. 

Like you I am not convinced it's a hardware issue. But the more info I have the better.

Thanks,

---

### Post by TuxCrafter on 2006-12-29
ata2: command 0x35 timeout, stat 0x58 host_stat 0x61

I have this error when copying data to my hard disk when it happens and it does often the hole system is down and I have to manually reset.

It only happens when writing to my Maxtor DiamondMAX 10 SATA300 disk my other for disks behave ok


Did some debugging found mine problem.

I seems that I have different sata cables. (they look the same) 
SATA I and SATA II cabels.
My hard drive only works with SATA II cables. When I attached a new cables. to it it works. The cable itself is ok because I can use it by my other drives.

And it only happens with my Maxtor drive. Last one I will buy. :-D

---

### Post by ianhaycox on 2006-12-31
Well oddly my Maxtor drive on ata1 behaves OK, but the Western Digital drive on ata2 hangs the system. I didn't know about the SATA I and SATA II cables. I might try fiddling about with different cables.

I suspect it's something to do with the second 'port' of the SiS controller. But it is guesswork.

At the moment the issue is on the back-burner for me until a newer kernel is released. If it still does not work after that then I will put a bit more effort into tracking down the problem.

---

### Post by ianhaycox on 2007-01-24
Eventually it got to me and I decided to buy a new disk drive to isolate the problem.

The second problem drive, a Western Digital, had NTFS Windows + a couple of ext3 partitons on it. Booted into Windows showed no problems with either drive (the Maxtor or WD) but in Linux the WD drive kept killing the system and reporting errors in the log files.

Bought a new Maxtor to replace the WD drive and had no end of trouble copying the data off the old WD drive to the new Maxtor. Tried qparted, ntfsclone, tar, dd, cp, all sorts. Everything died, even with a LiveCD of qparted. Consequently I blamed the SIS driver in Linux.

Ironically, I did finally manage to copy the data by using Acronis True Image for Windows. Finger still pointed at the Linux SIS driver.

After much cable/disk/grub swapping got the new drive installed and everything back to normal dual boot status and data restored with the new Maxtor Drive. A few tests and everything is OK. Before large file transfers between devices always failed and now they work OK.

So I'm guessing that the Windows SIS driver is either more tolerant of a failing disk drive (the old WD) or the Linux SIS driver likes Maxtor disks better than WD disks.

Anyway, everything seems OK for the time being, and I've got a spare (potentially bust) Western Digital SATA disk in the spares drawer.

Hope this helps someone.

Ian

---

