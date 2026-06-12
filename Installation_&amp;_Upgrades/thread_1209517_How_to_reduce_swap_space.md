---
title: "How to reduce swap space?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by gskumar on 2009-07-10
I am new to UBUNTU. At the time of installing, I did not know the purpose of swap space and the size required. I have allocated 20GB for Swap, where as my RAM is 1.25GB. After reading article on swap and its purpose in this forum, I understood the purpose and the size required. Hence, I feel that the space allocated is much more than required. If I want to reduce this and  add it to main partition, how do I do it?

---

### Post by csabo2 on 2009-07-10
A quick google goes a long way :)

[http://ubuntuforums.org/showthread.php?t=806973](http://ubuntuforums.org/showthread.php?t=806973)

---

### Post by starcraft.man on 2009-07-10
> **gskumar said:**
> I am new to UBUNTU. At the time of installing, I did not know the purpose of swap space and the size required. I have allocated 20GB for Swap, where as my RAM is 1.25GB. After reading article on swap and its purpose in this forum, I understood the purpose and the size required. Hence, I feel that the space allocated is much more than required. If I want to reduce this and  add it to main partition, how do I do it?

You'll need GParted. Good partitioning program. You can't do this while booted into Ubuntu (you'll be modifying the root directory or home I imagine, both in use), so I'd simply recommend you use the Live Desktop CD of your flavor of Ubuntu to do it.

1. Boot the Live CD.
2. System > Administration > Gparted/partitioner.
- If it isn't listed (seems to change with releases, I'm not sure) you can install it from the repositories with the following command. Open terminal Applications >Accessories > Terminal then type and enter:
```
sudo aptitude install gparted
```
3. Use the partitioner to resize the swap space and add to whatever partition you desire.
- [Documentation here]("http://gparted.sourceforge.net/documentation.php") if your unfamiliar.

If there's any trouble feel free to ask questions, ya can browse to the forums in the live CD long as your connected to the net.

Use the [gparted live stable CD]("http://gparted.sourceforge.net/download.php") if you lack the net at the time of the operation.

Note: As indicated by csabo, a quick search of the forums before posting a request can usually lead you to others who might have asked the same. Top right of the forums.

---

