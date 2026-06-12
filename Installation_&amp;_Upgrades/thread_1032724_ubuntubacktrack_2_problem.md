---
title: "ubuntu/backtrack 2 problem"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by FetalShinobi on 2009-01-06
ok so i been using ubuntu for about a year now just cause i dont like windows and i ran into backtrack doing some school research. i partitioned my harddrive into 5 (ubuntu being the main) then having 2 linux swaps and two empty partitions (bout 17 gigs each) i ran the backtrack cd and installed it to the empty partition....i had to restart the computer and when i did it went straight to backtrack and at that it had some kind of problem and wouldnt let me tru.....what should i do? i want to have an option as to which os i use.....o and if you guys havent figured it out im completely new to this kind of talk lol.....thanks in advance....

---

### Post by cariboo on 2009-01-06
Backtrack uses lilo as boot loader and Ubunut uses grub, you will have to use the LiveCD to reinstall grub. For a howto go [here]("http://ubuntuforums.org/showthread.php?t=224351"). Once you have grub working again you will have to add an entry for backtrack.

Jim

---

### Post by FetalShinobi on 2009-01-06
ok so i re-installed ubuntu and i got the other partitions...i havent tried to install backtrack 2 again cuz im wondering....do i fix the grub before or after i install backtrack?

---

### Post by FetalShinobi on 2009-01-08
ok so i re-installed ubuntu and i got the other partitions...i havent tried to install backtrack 2 again cuz im wondering....do i fix the grub before or after i install backtrack?

---

