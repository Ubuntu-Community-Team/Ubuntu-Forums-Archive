---
title: "SDHC Card not mounted on my EEEpc"
date: 2009-03-06
forum: Hardware
---

### Post by Krysa on 2009-03-06
I bought a 4GB SDHC card for my EEEpc.
When I insert it, he can't mount it.

I try to translate it properly:

bad superblock on /dev/sdb1
missing help program, invalid option, missing codepage....

try dsmesg|tail to view log.

ok bad translation but it is the best I can do.

log says:

root@leon-laptop:/home/leon# dmesg|tail
[  317.246016] sd 2:0:0:0: [sdb] Write Protect is off
[  317.246038] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  317.246061] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  317.256216] sd 2:0:0:0: [sdb] 7744512 512-byte hardware sectors (3965 MB)
[  317.257480] sd 2:0:0:0: [sdb] Write Protect is off
[  317.257506] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  317.257521] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  317.257548]  sdb: sdb1
[  317.905248] UDF-fs: No partition found (1)
[  317.980411] ISOFS: Unable to identify CD-ROM format.
root@leon-laptop:/home/leon# 

Hope you guys can help me out...

Thanks:)

---

