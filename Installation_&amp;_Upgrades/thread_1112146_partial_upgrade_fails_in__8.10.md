---
title: "partial upgrade fails in  8.10"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by gacostac on 2009-03-31
Hi, I have some updates waiting, but when upgrade manager runs it tells me it has to do a partial update. When i click continue it starts running and suddenly it vanishes from the screen.... nothing is updated and i still have the updates pending. What can i do? I have a 64bit  dell studio 
Thanks

---

### Post by cariboo on 2009-03-31
If you can't wait for the dependencies to show up, you can open an Applications-->Accessories-->Terminal and type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

This will only update the files that have all the dependencies met.

Jim

---

### Post by Evagrios on 2009-04-08
I have the same exact problem. I can get the upgrades if I do the manually, but it is really annoying to have to do it every time. As far as I can see there are two problems here and a solution to either would be helpful

1. some updates won't dowload because of unmet dependencies

2. the partial upgrade crashes.

---

### Post by f1ice on 2009-05-07
Thanks cariboo907.  That solved my problem.  I kept having a request for a partial upgrade yet it just disappeared when I started it.  Once again, thank you.

---

