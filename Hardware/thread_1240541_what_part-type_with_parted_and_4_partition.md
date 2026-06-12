---
title: "what part-type with parted and 4 partition"
date: 2009-08-14
forum: Hardware
---

### Post by laode on 2009-08-14
Hi,

I try to configure an empty 500 G HDD with 5 partitions, each 100 G and ext3.
I'm not well experienced with parted, but think there is a nice misleading in the docu:

"...part-type is one of: primary, extended, logical.  Extended and logical are only used for msdos and dvh disk labels..."

to create a partition (after labeling HDD to gpt), I follow this syntax:

**mkpart** part-type [fs-type] start end

I am confused now, what part-type do I need for Linux ?

If I use 4 times 'primary', what part-type shall I use for patition 5, since other types are not for Linux ?

thanks for any tip, Laode

---

### Post by jms1989 on 2009-08-14
the forth primary partition needs to be the extended partition, then you can add up to 64 logical partitions.

Example:

|- Partition 1 - 100GB - sdb1
|- Partition 2 - 100GB - sdb2
|- Partition 3 - 100GB - sdb3
|- Extended Partition - 200GB - sdb4
|---- Logical Partition 1 - 100GB - sdb5
|---- Logical Partition 2 - 100GB - sdb6

You will then have 5 partitions to use as needed. Hope this helps, cheers!

Oh, and btw, if you'd like, you can try gparted. It's the gui to parted. :)

---

