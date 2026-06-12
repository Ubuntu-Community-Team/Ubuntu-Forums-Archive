---
title: "Changing USB drive to read/write from read only"
date: 2022-05-26
forum: Hardware
---

### Post by Joe_Linux on 2022-05-26
I have a 16GB Eaget V66 USB drive. [ATTACH=CONFIG]290525[/ATTACH] see image. It is now read only and I have not been able to change it back to read/write.
```
joe@joe-GA-78LMT-USB3:~$ sudo hdparm -R1 /dev/sdb

/dev/sdb:
 setting write-read-verify to 1
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 write-read-verify = not supported
joe@joe-GA-78LMT-USB3:~$ 

```

Any thoughts or did I brick it ?

Thank you

---

