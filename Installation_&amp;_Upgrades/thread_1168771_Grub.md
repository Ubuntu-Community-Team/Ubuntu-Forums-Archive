---
title: "Grub?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by jrhartley on 2009-05-24
Ive been running XP on a machine that has 3 hard drives and Ive decided to add Ubuntu. the options I get during install are to add it side by side or use largest space available or use entire disk. the latter is the one I chose. well it seems ok as far as linux is concerned but grub menu errors when I select XP. I can get to xp by changing boot disks in BIOS but thats alot of work when I want to switch between the 2 OS's. is there a way to fix grub to make xp available(not good with linux)or maybe reinstall and select different option.....thanx

---

### Post by cariboo on 2009-05-24
IF you selected use entire disk when partitioning, you may not have an xp partion anymore. Could you open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and paste the results in your next post.

---

### Post by jrhartley on 2009-05-24
in the original post I said I had 3 different hard drives in the computer. I used 1 for ubuntu and the other 2 for XP. I can get into xp thru Bios by selecting that drive so the partition must be ok or I cant boot ubuntu by selecting that drive.....

---

