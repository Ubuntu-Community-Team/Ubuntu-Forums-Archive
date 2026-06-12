---
title: "Write to external hdd (NTFS)?"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by Bluecircle on 2007-05-13
I have an external 500gb hard drive connected to my computer through USB. I keep all my data on it and and need to write to it. It is formatted as NTFS so I assume that is why Ubuntu sees it as read only. How can I make it writable? Is there a safe way to convert it from NTFS to Ext3? I would like both Windows and Linux computers to be able to see and use it, so should I make it Fat32? Or is there an easier way?

Eg. can Linux write to NTFS drives in any (safe) way?

---

### Post by raylu on 2007-05-13
I'd recommend FAT32 for externals. Windows has a command-line utility called convert that works for FAT32->NTFS, but I don't know if it works in the other direction.

You've probably heard this, but there is at least one Linux tool to write to NTFS, but you risk data loss.

How much data is on the external? Is taking everything off, formatting it, and putting it back on an option?

---

### Post by Bluecircle on 2007-05-13
Around 300GB of data. It's actually 2 500GB drives in a RAID. It's the Maxtor OneTouch 1TB external USB hard drive.

---

### Post by raylu on 2007-05-13
Oh, I forgot. Linux has gparted, qtparted, and parted (try them in that order if you're using Ubuntu); they can convert some partition types. Again, I don't know if NTFS can be converted to anything without losing the data. They will tell you, though.

---

### Post by Bluecircle on 2007-05-13
Ok, I installed ntfs-config, and now it writes fine.

---

