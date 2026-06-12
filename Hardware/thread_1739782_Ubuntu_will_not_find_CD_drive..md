---
title: "Ubuntu will not find CD drive."
date: 2011-04-26
forum: Hardware
---

### Post by zozza on 2011-04-26
Hello,

I have an external CD drive which works fine in XP.  Ubuntu 10.04, however, will not find it. 

Dmesg shows:

[  255.950512] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  255.950527] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  255.950542] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  255.950558] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  255.950589] end_request: I/O error, dev sr0, sector 0

I have read that one solution is to add all_generic_ide=1 to /etc/defaults/grub then update-grub.  I did this and rebooted but obtain the same errors. 

Any ideas?  Thanks.

---

