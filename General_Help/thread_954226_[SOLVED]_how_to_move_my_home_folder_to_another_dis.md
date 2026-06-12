---
title: "[SOLVED] how to move my home folder to another disk"
date: 2008-10-21
forum: General Help
---

### Post by sandy8925 on 2008-10-21
Currently I have Ubuntu installed on a 4.7 GB partition and I have only about 400 MB left.

I installed another hard disk and formatted it to create a 25 GB ext3 partition.

My question is this:

I want my Ubuntu installation to use the 25 GB partition for installing apps and storing other data.How do I do this ?
Any help would be appreciated :)

---

### Post by kaibob on 2008-10-21
The following guide explains how to have your home directory on a different partition:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Applications have to go on the partition with the Ubuntu file system.

---

### Post by dcstar on 2008-10-21
> **sandy8925 said:**
> Currently I have Ubuntu installed on a 4.7 GB partition and I have only about 400 MB left.
.........

Apart from the excellent advice to have a separate /home partition, clean out your downloaded packages cache (via Synaptic) and you should get a fair amount of disk space back.

---

### Post by mir123 on 2010-02-04
If you don't want to lose the modification time for your files, add 

--preserve-modification-time

to your cpio command:

find . -depth -print0 | cpio --null --sparse --preserve-modification-time -pvd /new/

---

