---
title: "I want to write to my hard drives!"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by tjoel99 on 2007-09-03
On my computer I have sda1, sda5, and sda6.  sda6 is small and 97% filled.  The others are big and empty because I can't write to them.  I can't copy and paste onto them or write a document on to them because they are read-only.  I don't know why they are read-only.  Can anybody tell me how to make a hard disk fully write-able?  Thank you.

By the way, this system is dual-boot Windows XP and Ubuntu Christian Edition 3.3 (based on 7.04).

---

### Post by merlinus on 2007-09-03
If the partitions are NTFS, this should work:

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

