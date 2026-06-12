---
title: "Unable to reformat HD becoz of Ubuntu partition"
date: 2008-09-30
forum: General Help
---

### Post by kris2pe on 2008-09-30
I am unable to reformat my other hd to xp becoz I have ubuntu partition. And unfortunately Xp requires me to reformat my ubuntu partition as well just so I can make this work! 
Is there a solution to this?

---

### Post by prshah on 2008-09-30
> **kris2pe said:**
> I am unable to reformat my other hd to xp becoz I have ubuntu partition. And unfortunately Xp requires me to reformat my ubuntu partition as well just so I can make this work! 
Is there a solution to this?

Boot off the Ubuntu live CD, run the partition editor (System-Administration-Partition Editor), right click each partition entry that you want to delete, and choose "unmount" or "swapoff". Then right click it again and choose "delete". Once you are done, click "Apply" to commit your changes. Shutdown, reboot with your Windows CD and setup your Windows partitions as you like.

---

### Post by kris2pe on 2008-10-01
ok I'm a bit confuse coz I have 2 hds! 
One has an ubuntu partition and the other has an xp partition. 
I want to reformat my xp hd/partition! 
How do I go about that? 
Note I do not want to delete my ubuntu partition!

---

### Post by TheLions on 2008-10-01
it is same procedure as @prshah described but it can be done without LiveCD, also you'll need to install gparted if you haven't already

```
sudo apt-get install gparted
```

---

