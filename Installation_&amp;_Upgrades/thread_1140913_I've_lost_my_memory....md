---
title: "I've lost my memory...?"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by paddymoo on 2009-04-28
hello there!
its exciting this ubuntu thing, i feel a bit like i have discovered a little secret, and having my computer use my first non-windows OS is like learning a new language....
 
so heres my first problem.
 
i took the plunge and installed ubuntu Netbook remix on my acer aspire, which already had windows XP on it, so they now dual-boot and give me the choice on startup. The computer was new, and came with 160Gb HDD. Now, when i tried to copy music/movies from my portable HDD onto my netbook, it says there isnt enough space. 
 
i think I need to change the partition sizing, but i am not sure. Anybody got any easy fixes ?
 
whilst i am at it, is there anything else you would tell a first time user?
 
thanks
 
paddy

---

### Post by bapoumba on 2009-04-28
Please open a terminal (> Accessories > Terminal) and post the output to:
```
cat /etc/fstab
df -H
```

---

