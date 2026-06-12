---
title: "jaunty autologin + catalyst = issue"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by pandajaune on 2009-06-22
Hello,

first, excuse me if my english is not perfect. i will do my best to be as clear as posible.

i made a fresh install with jaunty and i chose the autologin option.
this is when i discovered ubuntu can boot without displaying gdm and asking for login and password.

wonderful moment that last only a few minutes because after having installed the catalyst all my hapiness went away.
all the aulogin process was upside down. the screen was full of green pixels and gdm was back... but with the 10 sec autologin timeout.

is it a bug?

i decided to use the radeonhd drivers available in the repository to keep this fast autologin but i lost all the 2d/3d features of my hd3850.

does the catalyst 9.6 fix this issue? i can't install and test them because i would to reinstall jaunty to recover the autologin features.

thanks by advance for your advice

ps : for those who own the same card, which driver do you use?

---

### Post by sola on 2009-06-30
I have this problem with an nvidia card so I don't think it is ATI / catalyst related.

It is hard to believe that such a basic feature is simply broken in Ubuntu but it seems to be true.

---

### Post by sola on 2009-07-12
Still no solution for the broken autologin feature. Extremely annoying.

It was suggested that it may be a problem with the "readahead" package but I removed it and auto login still didnt work after a full restart so I put it back.

---

