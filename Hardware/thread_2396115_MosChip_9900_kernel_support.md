---
title: "MosChip 9900 kernel support"
date: 2018-07-11
forum: Hardware
---

### Post by JeffNBNB on 2018-07-11
The subject card is a PCIe card with four serial ports and one parallel . There are two IC’s: MCS9900 and MCS 9922. It has worked for years, but recently stopped after a software update. Still works fine in Win 10. 


There is a bug report with a similar problem with similar issues:
[https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1578147.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1578147.html)


As the bug reporter suggests, I have downloaded the vendor driver and did:

```
make

```

and 

```
insmod 99xx.ko 


```

and no go. I tired an older live CD (kernel 4.8) and it works fine. 

Here are some command outputs:

```
$ uname -a
Linux Precision-T3600 4.15.0-24-generic #26~16.04.1-Ubuntu SMP Fri Jun 15 14:35:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
$lspci -v
....
07:00.0 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
    Subsystem: Device a000:3002
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at b050 [size=8]
    Memory at fa207000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b040 [size=8]
    Memory at fa206000 (32-bit, non-prefetchable) [size=4K]
    Memory at fa205000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


07:00.1 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
    Subsystem: Device a000:3002
    Flags: bus master, fast devsel, latency 0, IRQ 5
    I/O ports at b030 [size=8]
    Memory at fa204000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b020 [size=8]
    Memory at fa203000 (32-bit, non-prefetchable) [size=4K]
    Memory at fa202000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


07:00.2 Communication controller: MosChip Semiconductor Technology Ltd. Device 9900
    Subsystem: Device a000:2000
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at b010 [size=8]
    I/O ports at b000 [size=8]
    Memory at fa201000 (32-bit, non-prefetchable) [size=4K]
    Memory at fa200000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
....




```

How can I get this card working again? 

Thanks,
Jeff

---

