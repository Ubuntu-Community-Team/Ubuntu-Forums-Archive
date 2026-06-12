---
title: "RAID advice"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by malfist on 2008-01-12
I recently bought a 250 GB SATA II hdd and a Promise SATA/300 TX4, and I was wondering. My current harddrive is 200GB. Is there a way to mirror the 200GB on each hard drive and then use the additional 50GB for something else, that is not backed up?

---

### Post by MobiusNZ on 2008-01-12
Yeah I think your raid utils (bios) will let you create a mirror up to 200gb then o/s should pick up the other 50gb and address it natively.
Two problems though:

Depending on the raid card, it may require special software (drivers) to be able to do this (ie, its a software raid). The software could then limit whether you can still access your extra 50gb

Creating a raid will destroy your current partitions. So you need to back up all your current 200gb to somewhere else, create the raid, then reload it back on.

---

### Post by Toet on 2008-01-12
With linux software raid, you can do anything.

---

### Post by MobiusNZ on 2008-01-12
> **Toet said:**
> With linux software raid, you can do anything.
One thing to note though, is linux software raid and windows software raid don't normally mix. Ie you cannot dual boot without losing lots of hair. This may or may not be a crucial factor.

---

### Post by malfist on 2008-01-12
> **MobiusNZ said:**
> Yeah I think your raid utils (bios) will let you create a mirror up to 200gb then o/s should pick up the other 50gb and address it natively.
Two problems though:

Depending on the raid card, it may require special software (drivers) to be able to do this (ie, its a software raid). The software could then limit whether you can still access your extra 50gb

Creating a raid will destroy your current partitions. So you need to back up all your current 200gb to somewhere else, create the raid, then reload it back on.

I have to format the 200GB HDD too?
The TX4 has the ability to do some XOR work but it relies on the host CPU for basicly everything else.

As to dual booting with windows, I have a windows partition for Visual Studio Pro, and for Rome Total War. Can I set a partition (maybe that extra 50GB) to be a windows partition for a VMWare or something? I've never set up a VM.

---

### Post by MobiusNZ on 2008-01-12
> **malfist said:**
> I have to format the 200GB HDD too?

Yep.

> **malfist said:**
> Can I set a partition (maybe that extra 50GB) to be a windows partition for a VMWare or something?
You might be able to use the 50GB as a standard windows partiton if the raid only takes the first 200GB. My point was that windows won't recognise linux software raids, and linux won't recognise windows software raids and they may try to overwrite each other.

---

### Post by malfist on 2008-01-12
200 GB is a lot to back up...

---

