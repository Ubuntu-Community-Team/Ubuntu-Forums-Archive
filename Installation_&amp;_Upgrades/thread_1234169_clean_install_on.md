---
title: "clean install on /"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by paloalto71 on 2009-08-07
I have three partitions: /, /home, and swap

I would like to make a clean install of 9.04 on /
Will it affect in some ways my /home? can I during the manual install just select /?

Thanks!

---

### Post by drs305 on 2009-08-07
In step 4 (Partitioning) of the install, you can select manual partitioning. Select your existing /home partition as "/home" and make sure you *_do not_* mark it for partitioning. That will leave it undisturbed but retain it as your /home partition in the new fstab.

---

