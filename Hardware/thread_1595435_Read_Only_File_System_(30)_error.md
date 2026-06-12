---
title: "Read Only File System (30) error"
date: 2010-10-13
forum: Hardware
---

### Post by res55 on 2010-10-13
Hi


 I use an acer aspire 7730 notebook running Kubuntu 9.04 happily since a year.  
 In the last few days once or twice a day this notebook issues suddenly this error „read only file system (30)“ and I can not save anything on my home drive. After reboot this is fine again. But after a few hours (or quicker) it comes back.
 These are the last messages from var/log/messages after such reboots:
 

```
Oct 13 13:56:02 notebook2009 kernel: [ 2034.324341] ata5: hard resetting link
 Oct 13 13:56:05 notebook2009 kernel: [ 2036.972096] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
 Oct 13 13:56:05 notebook2009 kernel: [ 2037.372224] ata5.00: _GTF unexpected object type 0x1
 Oct 13 13:56:06 notebook2009 kernel: [ 2037.804189] ata5.00: _GTF unexpected object type 0x1
 Oct 13 13:56:06 notebook2009 kernel: [ 2037.804372] ata5.00: configured for UDMA/133
 Oct 13 13:56:06 notebook2009 kernel: [ 2037.804404] ata5: EH complete
 Oct 13 13:56:06 notebook2009 kernel: [ 2037.804550] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
 Oct 13 13:56:06 notebook2009 kernel: [ 2037.804608] sd 4:0:0:0: [sdb] Write Protect is off
 Oct 13 13:56:06 notebook2009 kernel: [ 2037.804675] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 Oct 13 13:57:10 notebook2009 kernel: [ 2102.084418] __ratelimit: 9 callbacks suppressed
 Oct 13 13:57:10 notebook2009 kernel: [ 2102.084427] nepomukservices[5616]: segfault at 4 ip b7e84a02 sp bfd53c10 error 4 in libQtCore.so.4.5.0[b7e31000+238000]
 Oct 13 13:57:30 notebook2009 nagios3: Caught SIGTERM, shutting down...  
 Oct 13 13:57:39 notebook2009 squid[4316]: Squid Parent: child process 4319 exited with status 0
 Oct 13 13:57:43 notebook2009 exiting on signal 15
 Oct 13 13:59:40 notebook2009 syslogd 1.5.0#5ubuntu3: restart.
 


 Or this
 


 Oct 13 13:09:21 notebook2009 kernel: [17134.209138] ata5: hard resetting link
 Oct 13 13:09:24 notebook2009 kernel: [17137.056093] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
 Oct 13 13:09:24 notebook2009 kernel: [17137.459226] ata5.00: _GTF unexpected object type 0x1
 Oct 13 13:09:24 notebook2009 kernel: [17137.897190] ata5.00: _GTF unexpected object type 0x1
 Oct 13 13:09:24 notebook2009 kernel: [17137.897370] ata5.00: configured for UDMA/133
 Oct 13 13:09:24 notebook2009 kernel: [17137.897406] ata5: EH complete
 Oct 13 13:09:24 notebook2009 kernel: [17137.897579] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
 Oct 13 13:09:24 notebook2009 kernel: [17137.897621] sd 4:0:0:0: [sdb] Write Protect is off
 Oct 13 13:09:24 notebook2009 kernel: [17137.897687] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```
 Who can translate this chinese? :popcorn: Is my HDD defect? :mad:

 Yours
 Res

---

### Post by res55 on 2010-10-13
now it seems to happen earlier.
Please help quickly, what should I do?

the root and home is on /dev/sdb1 
with 306 GB free space 67% of 458 GB
and 29 mio free nodes (-45%) of 30 mio

thanks in advance!
Res

---

### Post by res55 on 2010-10-14
Could it be, that this shows disk errors?
I wonder, what it is.

Res

---

