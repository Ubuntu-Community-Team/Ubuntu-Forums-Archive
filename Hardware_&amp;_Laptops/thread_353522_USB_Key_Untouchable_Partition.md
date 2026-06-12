---
title: "USB Key Untouchable Partition"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by thePsychologist on 2007-02-04
After using Ubuntu for about 1.5 months, this is the first problem I came across that I couldn't solve searching Google.

I have a 1GB USB key, and it has a FAT32 partition which is the main part of it. But then there seems to be this extra partition which is about 1.5 mb and stores the key's manual and some old Windows drivers. I can write to this little partition or whatever it is and delete stuff from it. Is there any way to get rid of it? It doesn't show up in fdisk:

```

Command (m for help): p

Disk /dev/sda: 1007 MB, 1007157248 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+   b  W95 FAT32


```

There's also something like that on my external hard drive.

---

### Post by thePsychologist on 2007-02-04
Update: It seems I can access this partition under /dev/sdb. So I go

fdisk /dev/sdb

And then I use the "p" command to get this:

```

Command (m for help): p

Disk /dev/sdb: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   623257122   679486963    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(623257121, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(679486962, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   567173161  1190466982   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(567173160, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(1190466981, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?         858         858           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(857, 0, 3)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(857, 0, 2)
Partition 3 does not end on cylinder boundary.
/dev/sdb4               1  1145037824  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(1145037823, 0, 3)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

My new guess is this part of the USB key might be differently physically somehow?

---

