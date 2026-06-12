---
title: "Partition fun"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by jnewbern on 2007-08-11
OK so for awhile i was using both windows and ubuntu on my machine but now i want to switch over completely. I have formatted my ntfs partition and I want to combine it with my linux storage partition. so here is the setup as of right not

sda1 (was my old ntfs partition)
sda2 /
sda3 swap
sda4 (my storage partition)

they are all ext3 now and what i would like to do is combine sda1 and sda4 and hopefully move sda2 to the front of the drive. Is this at all possible without loosing all my data? I have about 64 gigs of stuff i would like to keep and dont really feel like burning 18 or so dvds. any help would be appreciated.

---

### Post by greybit on 2007-08-11
Have you tried using the parted program?  I can't remember if it comes automatically installed with Ubuntu but if not you can install it in a terminal like so:

```

apt-get update
apt-get install parted

```

Then run parted from within the terminal.  If you type help while within parted you'll find its capabilities.  You can remove, create, and resize your partitions.

---

