---
title: "Expand /home with free space"
date: 2008-07-28
forum: General Help
---

### Post by RuleMaker on 2008-07-28
I deleted my windows partition and I'd like to add the free space to my linux ext2 partition without loosing any data, is that possible?

---

### Post by snowpine on 2008-07-28
Absolutely, you can do it with Gparted partition editor. If the deleted windows partition is next to your /home ext2, you can simply resize /home into the empty space. If they are not next to each other, you need to slide everything over to give /home room to expand.

As always, back everything up, move slowly and carefully, and make sure you understand what you are doing before you click Apply. :)

---

### Post by RuleMaker on 2008-07-28
Here I am on live CD...
Free space and my ext2 system partitions are next to each other but I am still unable to expand the size of my partition, here are the screenshots:

---

### Post by snowpine on 2008-07-28
Ok, sda2 is an "extended partition" that contains sda5 and sda6. So you have to resize sda2 first, then you should be able to resize the partitions inside it. :) Cool?

---

### Post by RuleMaker on 2008-07-28
Ok, I figured that out myself, thank you anyway!

---

