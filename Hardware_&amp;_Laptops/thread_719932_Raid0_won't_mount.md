---
title: "Raid0 won't mount"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Caislean on 2008-03-09
I have a PC with a dual 250gb hard drives set up in Raid0 that are plugged in to a Promise TK2300 PCI Raid card.

(Note: I followed info from the threads [here ]("http://ubuntuforums.org/archive/index.php/t-510328.html")and [here]("http://ubuntuforums.org/showthread.php?t=2557&page=1&pp=10") without luck.)

```

dmraid -r
/dev/sda/: pdc, "pdc_biffhcbjjc", stripe, ok, 488281250 sectors, data@ 0
/dev/sdb/: pdc, "pdc_biffhcbjjc", stripe, ok, 488281250 sectors, data@ 0

```

```

dmrait -tay
pdc_biffhcbjjc: 0 976562599 striped 2 128 /dev/sda 0 /dev/sdb 0

```

```

ls /dev/mapper
control

```
Shouldn't the drives show up in the ls output, such as "control pdc_biffhcbjjc pdc_biffhcbjjc1"?

Though I know it wouldn't work, I tried:
```

mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_biffhcbjjc /media/myraid
The device /dev/mapper/pdc_biffhcbjjc doesn't exit

```

The drives are working, as I can boot the machine in to Windows. But the Windows installation is corrupted and crashes for reasons we don't need to go in to here. I'm attempting to rescue data off the hard drives.

My two questions are...
[LIST=1]
[*]What am I doing wrong/missing in getting linux to recognize the drives?
[*]Will mounting the drives in linux mess up the data I'm trying to retrieve?
[/LIST]

---

### Post by diegosouza on 2008-03-09
I'm sorry Caislean but I only know about the mdadm, it's about software RAID.
Caislean, is only for hardware RAID the dmraid command?

---

