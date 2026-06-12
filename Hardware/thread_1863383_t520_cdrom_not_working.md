---
title: "t520: cdrom not working"
date: 2011-10-17
forum: Hardware
---

### Post by handverbrennung on 2011-10-17
Hi,

i just installed 11.10 on my thinkpad t520. Unfortunately the cdrom is not rcognized. So i had to install it with the net-install cd. I cant find it in the dmesg. What can i do?

Regards, enno

---

### Post by handverbrennung on 2011-11-09
DMESG shows

(...)
[239312.541093] ata2.00: hard resetting link
[239312.860423] ata2.01: hard resetting link
[239313.335520] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[239313.335546] ata2.01: SATA link down (SStatus 0 SControl 300)
[239313.335566] ata2.01: link offline, clearing class 3 to NONE
[239313.359572] ata2.00: configured for UDMA/100
[239316.461589] ata2.00: TEST_UNIT_READY failed (err_mask=0x2)
[239316.461603] ata2.00: limiting SATA link speed to 1.5 Gbps
[239316.461609] ata2.00: limiting speed to UDMA/100:PIO3
[239318.325097] ata2.00: hard resetting link
[239318.644434] ata2.01: hard resetting link
[239319.119533] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[239319.119559] ata2.01: SATA link down (SStatus 0 SControl 300)
[239319.119580] ata2.01: link offline, clearing class 3 to NONE
[239319.143582] ata2.00: configured for UDMA/100
[239320.963534] ata2.00: TEST_UNIT_READY failed (err_mask=0x2)
[239320.963537] ata2.00: disabled
[239320.963594] ata2.00: hard resetting link
[239321.282964] ata2.01: hard resetting link
[239321.758060] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[239321.758092] ata2.01: SATA link down (SStatus 0 SControl 300)
[239321.758119] ata2.01: link offline, clearing class 3 to NONE
[239321.758157] ata2: EH complete
(...)



strace lshw  ends up with

(...)
open("/dev", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 3
getdents(3, /* 212 entries */, 32768)   = 6280
getdents(3, /* 0 entries */, 32768)     = 0
close(3)                                = 0
open("/dev/cdc-wdm0", O_RDONLY|O_NONBLOCK

after that it just hangs. That should be my 3G-Module.

Any ideas?

---

