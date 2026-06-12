---
title: "Dual Boot - 2 hard drives"
date: 2010-03-06
forum: Hardware
---

### Post by collinge on 2010-03-06
I am using 9.10 on one hard drive and Xp on the other... I am tired of having to swap the hard drives around when I use one or the other.... any ideas?

---

### Post by louieb on 2010-03-06
What do you mean by swap around? physically? or in BIOS? 

If both a plugged in and your booted to Ubuntu - running 

```
sudo update-grub  
```

should add an XP entry to the GRUB2 menu.

---

### Post by collinge on 2010-03-13
Okay I tried that, nothing. Even tried changing my XP HD from CS to Slave.  I then booted to utility partion (grub) and XP still was not there.  How do I add it to that list.

---

