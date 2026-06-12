---
title: "partition sizes"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by amschmid on 2009-03-28
I am preparing to set up a dual boot of Vista and Kubuntu and want to make sure I understand correctly how I need to partition my hard drive. My goal is to give each operating system the space it needs while leaving as much space as possible to store data on a partition that they can both read/write.  Windows says that my hard drive is 107gb.  There is also a restore partition, but I don't plan to mess with that even though I plan to do a complete re-installation of Vista.  Here is my plan:

Vista- Primary partition, 20gb, NTFS (is this to big, is 15gb ok?)

Kubuntu- Logical partition w/ 2 extended partitions, Ext3
1. Swap partition 8gb (I have 4 gb RAM)
2. Root partition 10gb

Home (Shared)- Primary partition, 69gb (or whatever is left), Fat32

Is this a good plan?

---

### Post by zvacet on 2009-03-29
You don´t need 8 GB swap.It is waste of space because 1-2 GB should be enough,I will format shared partition as NTFS.Maybe somebody else will be more helpful then me.

---

