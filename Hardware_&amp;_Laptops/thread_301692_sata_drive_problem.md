---
title: "sata drive problem"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by wardjame on 2006-11-17
I added an additional 250Gb SATA drive to my Dapper Drake system using the eSATA connector provided with an external drive case.

The disk was recognized fine once I activated the second SATA connector in the BIOS.

I partioned the disk with fisk /dev/sdb creating a primary partition the full size of the drive.

I think tried to format the drive as ext3 with:
mkfs -t ext3 -v -c /dev/sdb1

It runs ok for a bit then I start getting a whole pile of errors like the following:
```

ata2: Command 0x25 timeout, stat 0xd0 host_stat 0x21
ata2: translated ATA stat/err 0xd0_00 to SCSI SK/ASC/ASCQ 0xb/47/00

```

My first thought is that my new hard disk is damaged.  Any suggestions on other methods to test the status of the drive itself?

---

### Post by gokusandwich on 2007-05-11
Hi.  Are you still having this problem?

I was running Dapper on my server, and I just upgraded it to Edgy a few weeks ago.  I hadn't yet rebooted it, so it has been running the old Dapper kernel until only a few minutes ago...

Today, before the reboot, I was having problems with writing to the filesystem that lives on that drive.  My syslog was filling up with messages like this:
```

ata2: command 0x25 timeout, stat 0xd0 host_stat 0x21
ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
ata2: status=0xd0 { Busy }
sd 1:0:0:0: SCSI error: return code = 0x8000002
sdb: Current: sense key: Aborted Command
     Additional sense: Scsi parity error
end_request: I/O error, dev sdb, sector 236867295
```

I've now rebooted, and am running on the Edgy kernel.  It seems to be working okay, but I don't trust the hard drive.  I guess I'll just see how it goes, since I have backups (I think).

---

