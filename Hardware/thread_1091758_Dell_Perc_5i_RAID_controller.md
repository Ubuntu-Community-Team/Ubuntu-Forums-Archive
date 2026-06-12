---
title: "Dell Perc 5/i RAID controller"
date: 2009-03-09
forum: Hardware
---

### Post by fadetoblack82 on 2009-03-09
i just built a new storage server with a perc 5i and had a question. im running 4x western digital black 1 TB drives in RAID5 off the perc 5i. the BBU is connected and my raid5 volume settings are: 64kb stripe size, write back, adaptive read ahead. i also flashed the card to the latest dell firmware. im running ubuntu 9.04 alpha 5 on the pc and it seems to recognize the card out of the box which is great.

```

ar@nas:~$ lspci | grep -i dell
03:0e.0 RAID bus controller: Dell PowerEdge Expandable RAID controller 5

```

so i made an ext4 partition on the volume using parted (didnt know fdisk had a 2TB partition limit) and setup a samba server so i could access it from my main pc. everything seems to work great, im getting great read/write speeds over the network. however, i did notice this in dmesg:
```

[  441.174932] sd 6:2:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[  441.174976] sd 6:2:0:0: [sdb] 5857345536 512-byte hardware sectors: (2.99 TB/2.72 TiB)
[  441.175030] sd 6:2:0:0: [sdb] Write Protect is off
[  441.175033] sd 6:2:0:0: [sdb] Mode Sense: 1f 00 00 08
[  441.175107] sd 6:2:0:0: [sdb] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA

```

i'm wondering about the last line specifically - i had set write back and adaptive read ahead in the perc bios, so why would it be saying read/write cache is disabled?

---

