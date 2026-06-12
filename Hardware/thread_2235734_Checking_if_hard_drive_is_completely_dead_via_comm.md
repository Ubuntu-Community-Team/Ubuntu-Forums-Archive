---
title: "Checking if hard drive is completely dead via command line"
date: 2014-07-22
forum: Hardware
---

### Post by dheianevans on 2014-07-22
Had one of the drives disappear from my Mythtv box while I was away and now I'm back from vacation with a summer cold. Since I'm a hacking, coughing sputtering mess right now, I don't feel like opening up the case to actually get close enough to hear if the drive is physically spinning.

fdisk -l doesn't show info for the XFS partitioned drive, while xfs_check and xfs_repair say they can't find the superblock. Since I don't know enough about those two utilities, I'm wondering if they'd just report they couldn't find the superblock if a) it wasn't there due to a disk error or b) wasn't there because the drive was deader than Lindsay Lohan's career.

Is there a utulity that just plain and simple reports which drives are actually physically spinning in your system?

Thanks.

---

### Post by steeldriver on 2014-07-22
If the disk supports SMART, then you could possibly use smartctl (from the smartmontools package) - I'm not an expert in its usage but at its simplest there's a 'basic health' test

```

sudo smartctl -H /dev/sda

```

---

