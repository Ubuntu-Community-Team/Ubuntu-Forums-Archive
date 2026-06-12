---
title: "Reiser-Partition Recovery"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by greirt on 2007-08-12
Today while using firefox suddenly my screen became black. I could still access to the pc via ssh from another but it didn't worked correcly. So I did an reset.

While booting grub stops with "Error 17". Now i run Knoppix from CD and start Testdisk. It stops with "Harddisk seems too small". I heard that the reason for than could be a Jumper-Problem. But I havent changed the jumpers.

I have tried reiserfsck too. I have written a new superblock block with it. But that seems not to be enough. I dont want to do a "reiserfsck --rebuild-tree" because I did it once with an other partition and i had to rename and move over 1000 of numbred files in 300 numbred folders. That is an alternative for me, but the last.

How to get my files (with right names) back?

--
and hit me for my english

---

### Post by greirt on 2007-08-13
I did the "reiserfsck --rebuild-tree" now. Some files are where there has to be. But the most of them are in "lost+found"but some very important file dont exist anymore *ahhh*

No chance to bring them back, because the rebuilt of the tree destroyed them??

---

