---
title: "Failing Hard Drive?"
date: 2008-05-07
forum: Hardware
---

### Post by fiftyMIPsparc on 2008-05-07
Lately I've been getting strange panel errors, applets killing themselves, random lockups... so I ran fsck with the scan for bad blocks switch and it throws out a bunch of errors like this:

```

[28032.292561] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[............] ata1.00: BMDMA stat 0x4
[............] ata1.00: cmd ... tag 0 dma 4096 in
[............] ata1.00: status { DRDY ERR }
[............] ata1.00: error: { UNC }
[............] ata1.00: Buffer I/O error on device sda1, logical block 16403334
```

This happens when scanning sectors towards the end of the drive. Is this a sign that my hard drive failing, or is it something else?

---

### Post by tamoneya on 2008-05-07
looks a little bit more like a corrupted partition to me.  Not positive though.

---

### Post by fiftyMIPsparc on 2008-05-14
Corrupted partition? How bad could it be if I'm still able to boot, read, and write most files normally? Is fsck fixing this for me, or are these just errors?

---

### Post by az on 2008-05-14
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

