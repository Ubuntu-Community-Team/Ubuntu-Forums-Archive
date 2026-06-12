---
title: "can I add this ram to my machine"
date: 2008-06-04
forum: Hardware
---

### Post by jjz8706 on 2008-06-04
Hi,

Pretty new to building computers and Ubuntu,

I recently got a used box and added a few things to it. It currently has 512MB ram, and I have another 512 stick I would like to add. How can I tell if the two types will be compatible and how can I check what kind is currently in the system without taking it out.

The extra stick I have is 512MB DDR PC2700 CL2.5. I took it out of an old HP desktop.

Thanks for any help.

---

### Post by Rocket2DMn on 2008-06-04
The best way to tell is to actually open the computer and look at what is written on the memory, or refer to documentation that came with the machine if possible.  This will surely tell you what RAM is compatible.  Alternatively, you can google the computer make/model and find some generic specs for the system which can tell you what type of memory is compatible.
Although this won't tell you the exactly memory type, it will give you some specs on it, run:
```
sudo lshw -C memory
```

---

