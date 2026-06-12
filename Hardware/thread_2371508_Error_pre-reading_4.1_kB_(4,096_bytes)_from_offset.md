---
title: "Error pre-reading 4.1 kB (4,096 bytes) from offset 0 bytes (g-io-error-quark, 0)"
date: 2017-09-15
forum: Hardware
---

### Post by HDTimeshifter on 2017-09-15
I've been having trouble copying files to this data hard drive (on my file server through local sharing) and a few times lately the drive won't mount. All the SMART data is OK, but when I try to run a Self-test, I get the error "sk_disk_smart_self_test: Operation not supported (udisks-error-quark, 0)". When I try to benchmark it in the disks utility, I get the error "Error pre-reading 4.1 kB (4,096 bytes) from offset 0 bytes (g-io-error-quark, 0)".

When researching the error copying files, I found some information regarding bad superblocks and ended up repartitioning and reformatting the drive a week ago, but am getting the above errors, which seems like the superblock is bad again, so I'm thinking the drive is bad. I don't really want to toss this 500 GB drive until I can run an extended self-text that reveals errors. Here's a link to my other thread: [https://ubuntuforums.org/showthread.php?t=2370323](https://ubuntuforums.org/showthread.php?t=2370323)

---

### Post by HDTimeshifter on 2017-09-15
I opened the case and made sure all the SATA cables were tight, then rebooted and was able to run a Short self-test. When I try to run a Conveyance or Extended test, I get the below errors: 

"Error refreshing SMART data
Error sending ATA command CHECK POWER MODE: Unexpected sense data returned:
0000: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................
0010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................
 (g-io-error-quark, 0)"

(2nd try after rebooting again)
"Error starting SMART self-test
sk_disk_smart_self_test: Operation not supported (udisks-error-quark, 0)"

So is the drive bad?

---

