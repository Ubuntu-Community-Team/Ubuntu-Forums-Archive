---
title: "Formatting old partitions, and remounting them."
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Blåbär on 2009-10-19
Hi.

I wanted to get 9.04 installed, the 32-bit version, instead of my previous 8.10 64 bit. Being the apprentice that I am, I installed it side-by-side with XP and 8.10.

Now I'd like to format 8.10 and merge/mount the partitions with either windows or 9.04 - any advice/guidance available?

/Bb.

---

### Post by Mark Phelps on 2009-10-19
Not aware of any Linux SW that actually "merges" partitions.  Know this has been requested as a feature in GParted for some time, but not aware of it being implemented yet.

If you're just looking for setting up a partition for sharing data, create an NTFS partition and allow both MS Windows and Ubuntu to access it.

---

### Post by Blåbär on 2009-10-20
How do I know what I have on what "mount"? I thought ntfs was where my current XP was at, so I didn't dare to format my old partitions when I wanted to install 9.04 - pretty shitty result not to set it up manually.

---

### Post by dabl on 2009-10-20
The two console commands to sort your drives/partitions are

```
sudo fdisk -lu
```

and

```
sudo blkid
```

To show what is already mounted, and where, you can issue ```
sudo mount
``` and observe the output.

---

