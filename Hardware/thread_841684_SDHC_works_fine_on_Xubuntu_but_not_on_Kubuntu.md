---
title: "SDHC works fine on Xubuntu but not on Kubuntu"
date: 2008-06-26
forum: Hardware
---

### Post by 801 on 2008-06-26
Hi All,

We have two EEEpcs over here, one running eeeXubuntu (mine) and one running Kubuntu Hardy (my wife's). Today two SDHC 8 GB cards arrived. When I plug either one into the eeeXubuntu machine it's mounted immediately, so both cards seem to be fine.
When I plug either card into the Kubuntu machine, first I get the standard "what to do" message, but when I try to open I get this message:

[quote]
mount: wrong fs type, bad option, bad superblock on /dev/sdb1.
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
[end quote]

this is the output I get from dmesg | tail:

[quote]
[ 4381.301306] sd 2:0:0:0: [sdb] Write Protect is off
[ 4381.301318] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4381.301324] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4381.303240] sd 2:0:0:0: [sdb] 15660032 512-byte hardware sectors (8018 MB)
[ 4381.304156] sd 2:0:0:0: [sdb] Write Protect is off
[ 4381.304167] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4381.304173] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4381.304188]  sdb: sdb1
[ 4381.410845] UDF-fs: No partition found (1)
[ 4381.464581] ISOFS: Unable to identify CD-ROM format.
[end quote]
(I'm sorry, the code button doesn't seem to work so I'm using quote instead)

Does anybody have an idea what's going on, and how to fix this? Thank you.

---

### Post by Odrodzona-Sarmacja on 2008-06-27
Xubuntu is smart choice. I run all my kde (kde-base) apps on it :)
Just a thought. Kubuntu misses some package maybe? O.O

---

### Post by 801 on 2008-06-27
Yeah well, that thought has occurred, but I'm not going to cross-check 980 packages. Searches with "disc", and "mount" and "fs" didn't help. Any other ideas?

---

