---
title: "Manually mount RAID1?"
date: 2011-07-30
forum: Hardware
---

### Post by Abaddon on 2011-07-30
Hi All,

I've got a recently completely upgraded 11.04 system that I dual boot Ubuntu and Windows on.  I had all sorts of dramas getting it up and running dual booting, but that's all fine now.

Around the same time as all this, I've had one of my backup drives crash so I've lost the easily accessible backup of my data.

I've got the old hard-drives from my previous system (2x 500Gb mounted in RAID1).  I need to mount the RAID so I can copy my old data off them.

How do I do this?

The RAID is recognised at:  /dev/mapper/isw_ddbcgagbib_RAID
The component drives are:  /dev/sdb and /dev/sdc

When I mount /dev/mapper/isw/ddbdgagbib_RAID I get a "nothing in fstab" entry - what do I need to do to get them to mount?

TIA.

---

### Post by mucho_maze on 2011-10-12
Can you mount them as /dev/md*? For instance:

sudo mount /dev/md0 /media/md0

---

