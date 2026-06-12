---
title: "Recovering partitions - Found them, but what to do?"
date: 2013-02-18
forum: Hardware
---

### Post by cyanide911 on 2013-02-18
This is what testdisk shows before 'Quick Search':

[IMG]http://i.imgur.com/tlUPEGx.png[/IMG]

You can see Gparted open as well.

This is what testdisk shows after Quick Search:

[IMG]http://i.imgur.com/Lv46zf7.png[/IMG]

As you can see it found the two missing EXT4 partitions.

The problem is, I can't figure out what to do after this. How do I actually recover those two partitions?

---

### Post by cyanide911 on 2013-02-18
I suppose I've to mark those drives as extended, primary or logical. I've no idea what to do with those.

Can someone help me, using the gparted screenshot as reference?

---

### Post by offgridguy on 2013-02-18
> As you can see it found the two missing EXT4 partitions.

Actually I can't see that, don't see any ext4 partitions.  Did you have a linux OS
installed, that is now removed?

---

### Post by oldfred on 2013-02-18
Gparted is just showing the unallocated. Testdisk shows two deleted Linux partitions. But testdisk still uses the old CHS cylinder, head, sector nomenclature, but it looks like they are in the right place. I might try just changing from D to Locigal as they have to be in the extended partition.

You do have good backups? Before any system changes you need the backups. While most of the time it just works, when it does not it makes for huge issues.

---

