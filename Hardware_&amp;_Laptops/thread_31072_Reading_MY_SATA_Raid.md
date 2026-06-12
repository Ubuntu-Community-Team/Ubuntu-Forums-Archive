---
title: "Reading MY SATA Raid"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by Kaiser_Sosae on 2005-05-01
Firstly, i know there are a million people, with a million problems with sata raids...

I have a sata raid 0 config, on this, i have made a partition of 25gb for linux... (through norton partition magic on my windows xp), the rest has windows xp on it.

MY linux, is installed in an IDE hdd... which is only 4gb (salvaged from my old, old computer), i just want this 25gb to come up, so i have some more space... 

How would i view the partition from linux?

-MIke

---

### Post by alastair on 2005-05-02
You might need to forget about BIOS level SATA RAID. Windows probably has a special driver for it, but Linux probably doesn't. Linux /can/ do SATA RAID though - but at the OS, not BIOS, level (i.e. use mdadm).

You might need to look to your BIOS. But be careful.

---

