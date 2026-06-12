---
title: "Grub error 22 with external HD plugged in"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by abroden on 2007-03-11
I've searched around for a while now, but not found anything quite what I'm looking for. Whenever I start my PC with my external hard drive plugged in, I get a GRUB error 22. If I remove the HD, it starts up fine and I can plug it in and access it without any problems once I'm past GRUB. Anyone know what causes this, and how to fix it?

Here's what my fdisk -l (with the external drive) looks like, if that's of any help:

```
Disk /dev/sda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        5100    40960048+   7  HPFS/NTFS
Partition 1 slutar inte på cylindergräns.
/dev/sda2            5101       19457   115322602+   b  W95 FAT32

Disk /dev/sdb: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1           19330       19457     1028160   82  Linux växling / Solaris
/dev/sdb2               1        6374    51199123+  83  Linux
/dev/sdb3            6375       19329   104061037+   b  W95 FAT32

Posterna i partitionstabellen är inte i diskordning

Disk /dev/sdg: 160,0 GB, 160041886208 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdg1               1       19457   156288321    7  HPFS/NTFS
```

---

