---
title: "Optiarc AD-7260S DVD RW drive not usable by Ubuntu"
date: 2011-06-11
forum: Hardware
---

### Post by ratcheer on 2011-06-11
I am having another problem with my new PC that seems to have many bug reports over several years, but no real fixes. When the PC arrived brand new five days ago, it had Windows 7 and the drive worked perfectly. But Ubuntu does not even have an entry for it in /dev. Until a little while ago, I thought the drive was undetected by Ubuntu. 

I finally found these messages in dmesg:

```

[    1.983919] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.03, max UDMA/100
[    2.023905] ata2.00: configured for UDMA/100
[    2.124189] ata2.00: TEST_UNIT_READY failed (err_mask=0x2)
[    7.816381] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.876412] ata2.00: configured for UDMA/100
[   12.869929] ata2.00: qc timeout (cmd 0xa0)
[   12.869933] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   12.869938] ata2.00: limiting SATA link speed to 1.5 Gbps
[   12.869941] ata2.00: limiting speed to UDMA/100:PIO3
[   13.728884] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   13.788912] ata2.00: configured for UDMA/100
[   18.782446] ata2.00: qc timeout (cmd 0xa0)
[   18.782450] ata2.00: TEST_UNIT_READY failed (err_mask=0x4)
[   18.782453] ata2.00: disabled
[   18.782472] ata2.00: hard resetting link
[   19.641387] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)

```The drive is a Sony Optiarc AD-7260S. It seems to have the current  firmware version 1.03. It also seems to have actually been manufactured  by NEC.

It is hard to use a PC without the CD/DVD drive working. Any help getting it to work would be very much appreciated.

I also started a question on Launchpad, #161106.

Thanks,
Tim

---

### Post by ratcheer on 2011-06-11
Solution was found in answer to my Launchpad question. I moved the DVD drive cable from a SATA III port to a SATA II port and the drive is now working in Ubuntu.

I am still somewhat puzzled, as the drive was working perfectly in Windows 7 while connected to a SATA III port.

Tim

---

