---
title: "Laptope problem at shutdown"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by analyzer on 2007-09-19
Hello

Sometimes my laptop (Lenovo ThinkPad T60) stops shutting down with the followed error messages in the syslog.

```
kernel: [ 1871.904000] ata1.00: exception Emask 0x2 SAct 0x7ff8003f SErr 0x0 action 0x2 frozen
kernel: [ 1871.904000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x7ff0003f FIS=005040a1:00040000)
kernel: [ 1871.904000] ata1.00: cmd 61/10:00:87:88:89/00:00:0b:00:00/40 tag 0 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:08:0f:89:89/00:00:0b:00:00/40 tag 1 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/10:10:1f:89:89/00:00:0b:00:00/40 tag 2 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/10:18:3f:89:89/00:00:0b:00:00/40 tag 3 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/10:20:97:89:89/00:00:0b:00:00/40 tag 4 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:28:cf:89:89/00:00:0b:00:00/40 tag 5 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:98:cf:86:89/00:00:0b:00:00/40 tag 19 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:a0:ef:86:89/00:00:0b:00:00/40 tag 20 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:a8:17:87:89/00:00:0b:00:00/40 tag 21 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:b0:27:87:89/00:00:0b:00:00/40 tag 22 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:b8:37:87:89/00:00:0b:00:00/40 tag 23 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/20:c0:bf:6b:8c/00:00:0b:00:00/40 tag 24 cdb 0x0 data 16384 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/10:c8:47:87:89/00:00:0b:00:00/40 tag 25 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:d0:af:88:89/00:00:0b:00:00/40 tag 26 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/10:d8:a7:87:89/00:00:0b:00:00/40 tag 27 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:e0:e7:87:89/00:00:0b:00:00/40 tag 28 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/10:e8:ff:87:89/00:00:0b:00:00/40 tag 29 cdb 0x0 data 8192 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
kernel: [ 1871.904000] ata1.00: cmd 61/08:f0:cf:88:89/00:00:0b:00:00/40 tag 30 cdb 0x0 data 4096 out
kernel: [ 1871.904000]          res 50/00:08:cf:89:89/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
```

```
uname -a
Linux std 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux 
```

Does somebody have an idea, how to fix?

Thanks a lot.

---

