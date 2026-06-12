---
title: "problem with Drive Image - Disk to Disk (Windows)"
date: 2008-07-30
forum: General Help
---

### Post by Puffin-ww on 2008-07-30
Dear all

My Drive Image 5.0 has only just started to have this problem:

When I try a "Disk to Disk" with Windows-partitions, I get:
"Error #510: The version of the file system is not supported."

This is the first time I wanted to do a "Disk to Disk" after I installed Ubuntu 8.04 (on a separate hard disk though). So I was wondering whether the installation of Ubuntu could somehow cause this problem.

Any ideas?

Thanks

Puffin-ww

---

### Post by prshah on 2008-07-30
> **Puffin-ww said:**
> 
My Drive Image 5.0 has only just started to have this problem:
When I try a "Disk to Disk" with Windows-partitions, I get:
"Error #510: The version of the file system is not supported."


If you have installed Ext2/3 IFS for Windows (allows access to Ubuntu's ext2/3 partitions from Windows) you can get this error, even if the partitions are not mapped to any drive letters.

I had the same problem with PartitionMagic 8 with Ext2/3 IFS drivers installed.

If you don't have ext2/3 ifs drivers installed, I have no idea what the problem is.

---

