---
title: "changing ubuntu partition"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by linux noooob on 2007-06-15
ok so i installed ubuntu with a partition of 10gb but know i want to delete my windows d partion and make the bear minimum for my windows xp c: partition. so i went to the live cd and started the partition manager only to find i could lower partitions but not increase them?? so how do i increase the ubuntu partition?

---

### Post by dreadlord_chris on 2007-06-15
> **linux noooob said:**
> ok so i installed ubuntu with a partition of 10gb but know i want to delete my windows d partion and make the bear minimum for my windows xp c: partition. so i went to the live cd and started the partition manager only to find i could lower partitions but not increase them?? so how do i increase the ubuntu partition?

I'm pretty sure the only way to increase the size is if there is free space ***right after*** it. Linux is all about options though, and in this case there is probably a better option. Consider using the freed up space as a seperate ***/home*** partition. That is where the greatest amount of file-system growth will tend to occur. By moving  ***/home*** to it's own partition it makes it that much harder to bork your system partition.
You can find a guide here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

