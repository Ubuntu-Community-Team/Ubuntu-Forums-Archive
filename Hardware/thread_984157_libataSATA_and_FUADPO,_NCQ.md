---
title: "libata/SATA and FUA/DPO, NCQ"
date: 2008-11-16
forum: Hardware
---

### Post by Cracauer on 2008-11-16
Geez, anybody knows where I can find a manpage-like thing for libata?

I'm building my new array (md-based) and I want NCQ on and the write-back cache on the disks off.

Controller is ata_piix, disks are Seagate 1 TB ES.2, so things should work with NCQ. 2.6.24 right now, 2.6.26 tomorrow.

However, inspecting boot messages I have a hard time figuring out what capabilities I have or can activate. So there's questions:

%%

What in the world are DPO and FUA?

How can I tell whether NCQ queuing is supported and/or active?

Here's the scoop:
```

scsi0 : ata_piix
scsi1 : ata_piix
ata1: SATA max UDMA/133 cmd 0x20c8 ctl 0x20e4 bmdma 0x20a0 irq 19
ata2: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e0 bmdma 0x20a8 irq 19
ata1.00: ATA-8: ST31000340NS, SN05, max UDMA/133
ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata1.01: ATA-8: ST31000340NS, SN05, max UDMA/133
ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata1.00: configured for UDMA/133
ata1.01: configured for UDMA/133
ata2.00: ATA-8: ST31000340NS, SN05, max UDMA/133
ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata2.01: ATA-8: ST31000340NS, SN05, max UDMA/133
ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata2.00: configured for UDMA/133
ata2.01: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      ST31000340NS     SN05 PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: unknown partition table
sd 0:0:0:0: [sda] Attached SCSI disk
sd 0:0:0:0: Attached scsi generic sg0 type 0
scsi 0:0:1:0: Direct-Access     ATA      ST31000340NS     SN05 PQ: 0 ANSI: 5
sd 0:0:1:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
sd 0:0:1:0: [sdb] Write Protect is off
sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:1:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
sd 0:0:1:0: [sdb] Write Protect is off
sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb: unknown partition table
sd 0:0:1:0: [sdb] Attached SCSI disk
sd 0:0:1:0: Attached scsi generic sg1 type 0
scsi 1:0:0:0: Direct-Access     ATA      ST31000340NS     SN05 PQ: 0 ANSI: 5
sd 1:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
sd 1:0:0:0: [sdc] Write Protect is off
sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 1:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
sd 1:0:0:0: [sdc] Write Protect is off
sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdc: unknown partition table
sd 1:0:0:0: [sdc] Attached SCSI disk
sd 1:0:0:0: Attached scsi generic sg2 type 0
scsi 1:0:1:0: Direct-Access     ATA      ST31000340NS     SN05 PQ: 0 ANSI: 5
sd 1:0:1:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
sd 1:0:1:0: [sdd] Write Protect is off
sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 1:0:1:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
sd 1:0:1:0: [sdd] Write Protect is off
sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdd: unknown partition table
sd 1:0:1:0: [sdd] Attached SCSI disk
sd 1:0:1:0: Attached scsi generic sg3 type 0

```

Thanks!

---

### Post by Cracauer on 2008-11-17
Bump.

So I figured I have NCQ, because performance is quite good with the write cache off.

But I'd still like to know what FUA and DPO are and why dmesg didn't say anything about me being NCQ capable.

---

### Post by ja7 on 2008-11-24
FUA/DPO is scsi parameters.

from man sg_read 

       dpo=0 | 1
              when set the disable page out (DPO) bit in SCSI READ commands is
              set.  Otherwise the DPO bit is cleared (default).

       fua=0 | 1
              when set the force unit access (FUA) bit in SCSI  READ  commands
              is set.  Otherwise the FUA bit is cleared (default).

from [http://en.wikipedia.org/wiki/SCSI_Read_Commands](http://en.wikipedia.org/wiki/SCSI_Read_Commands)

Disable Page Out (DPO) allows the initiator to warn the target that the data being read is unlikely to be requested again soon and so is not worth keeping in the target's data cache. 
Force Unit Access (FUA) tells the target to fetch the data from the media surface and to not use a cached copy.

ps. found your post while trying to find out what the FUA/DPO in my boot log was about.

---

### Post by deuxpi on 2008-12-03
Sorry, but it seems that even if your disk supports NCQ, your controller doesn't (and never will).

See the references [http://linux-ata.org/faq.html#ncq]("http://linux-ata.org/faq.html#ncq") about the information in the following line:

ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)

The "depth 0" line tells that NCQ is present (from the disk) but not enabled (because of missing hardware support).

The references [http://linux-ata.org/driver-status.html]("http://linux-ata.org/driver-status.html") or [http://ata.wiki.kernel.org/index.php/Hardware%2C_driver_status]("http://ata.wiki.kernel.org/index.php/Hardware%2C_driver_status") tells a bit more about this controller.

---

### Post by Cracauer on 2008-12-04
Ah bloody hell. I knew I had forgotten something.

The hardware can do NCQ all right, and under Linux.

But not if you are using the piix driver. You have to use the AHCI driver.

Now I already switched the system over :mad:

---

### Post by byteborg on 2009-02-15
Turn on AHCI in BIOS.
Probably you got "Standard-IDE" or similar selected in the BIOS IDE Setup.
Toggle it to AHCI mode and everything will be fine.

Ok, I lied: if you multi-boot to MS-Windos, your Windos installation will STOP at boot, probably even without a blue screen, with spontaneous reboot.

OTOH, your Seagate disk's Firmware might be problematic. IIRC, some drives require a firmware upgrade.
Look here: [http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963&Hilite=firmware](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963&Hilite=firmware)

All the best,
/k

---

### Post by Cracauer on 2009-02-15
> **byteborg said:**
> Turn on AHCI in BIOS.
Probably you got "Standard-IDE" or similar selected in the BIOS IDE Setup.
Toggle it to AHCI mode and everything will be fine.

Ok, I lied: if you multi-boot to MS-Windos, your Windos installation will STOP at boot, probably even without a blue screen, with spontaneous reboot.

OTOH, your Seagate disk's Firmware might be problematic. IIRC, some drives require a firmware upgrade.
Look here: [http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963&Hilite=firmware](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963&Hilite=firmware)

All the best,
/k

I solved it back then, I thought I had updated the thread.

But yes, just turning on AHCI in the BIOS and compiling in AHCI support does it instantly, because the AHCI drivers try to detect before the piix drivers. So all is fine and I get much better performance with the write cache off now.

It's impossible to figure out which drives,, exactly, need the firmware upgrade with these Seagate losers. I'll update some day, but alas these things never powercylce in the first place.

---

