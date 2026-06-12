---
title: "Cardreader - just an empty Filesystem"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by b0rsten on 2007-01-11
Hi,
I own a DELL pc with a build-in cardreader. But when i insert a "Sony MemoryCard", ubuntu doesn't mount it and when i take a look with gparted at the filesystem, the only thing i see is an empty memorycard without a filesystem, and i can't create one.

The card works fine in my camera, handy and my printer, so the problem is the software or the cardreader ;(

```

# tail -f /var/log/messages
Jan  9 14:08:29 localhost kernel: [17204311.092000] end_request: I/O error, dev sdd, sector 0
Jan  9 14:08:29 localhost kernel: [17204311.120000] end_request: I/O error, dev sdd, sector 0
Jan  9 14:08:29 localhost kernel: [17204311.152000] end_request: I/O error, dev sdd, sector 0
Jan  9 14:08:29 localhost kernel: [17204311.188000] end_request: I/O error, dev sdd, sector 0
Jan  9 14:08:29 localhost kernel: [17204311.220000] end_request: I/O error, dev sdd, sector 0
Jan  9 14:09:00 localhost kernel: [17204341.800000] SCSI device sdd: 1986560 512-byte hdwr sectors (1017 MB)
Jan  9 14:09:00 localhost kernel: [17204341.832000] sdd: Write Protect is off
Jan  9 14:09:00 localhost kernel: [17204341.868000] SCSI device sdd: 1986560 512-byte hdwr sectors (1017 MB)
Jan  9 14:09:00 localhost kernel: [17204341.888000] sdd: Write Protect is off
Jan  9 14:09:00 localhost kernel: [17204341.892000]  sdd:end_request: I/O error, dev sdd, sector 0
Jan  9 14:09:00 localhost kernel: [17204341.916000] printk: 13 messages suppressed.
Jan  9 14:09:00 localhost kernel: [17204341.944000] end_request: I/O error, dev sdd, sector 0
Jan  9 14:09:00 localhost kernel: [17204341.944000]  unable to read partition table
Jan  9 14:09:00 localhost kernel: [17204341.992000] end_request: I/O error, dev sdd, sector 0 

```

any ideas how to solve the problem?

---

