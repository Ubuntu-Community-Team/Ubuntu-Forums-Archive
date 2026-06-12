---
title: "hald fails to start after update"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by beuno on 2006-05-31
I've fixed a lot of problems just browsing the forums, so I'm going to go ahead and post the problem I had and how I fixed it.
For some strange reason, around 3 weeks ago I updated 5 PCs at the office which had Dapper flight 4-6 (all different ones), and after the dist-upgrade, which went smoothly btw, all the PCs hung up after a restart on loading the HAL deamon (hald).
I reinstaled with BETA 2 after a week or so on one of the PCs (the others just went to work to windows), and updated the fresh install.
Again, broken.
Did it a third time a week later, and still the same thing.
Finally, I was on Dapper RC1 and had resisted the temptation to update till today, where I did it again, and again, broke.
How did I fix it?

sudo dpkg --configure -a

For some reason it seems it doesn't install and configure all the packages correctly.
I haven't seen anyone complaining about this here, so I assume it's not that common, but it does happen with PCs over here :-?

---

