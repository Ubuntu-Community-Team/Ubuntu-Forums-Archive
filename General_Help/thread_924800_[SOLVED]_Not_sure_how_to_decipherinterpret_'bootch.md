---
title: "[SOLVED] Not sure how to decipher/interpret 'bootchart' images..."
date: 2008-09-19
forum: General Help
---

### Post by Predator106 on 2008-09-19
Hello, I have a bootchart image, from the 'bootchart' or 'bootchartd' think it's the latter, but anyways, I don't know what it really stands for...

Apparently the legends they give are really confusing/not enough information, I have no idea of how to tell what is preventing shutdown or startup, etc. from being fast/holding it up.

Here is the one I'm looking at...

Could anyone explain this to me? I couldn't find anything, even this guide ' [http://aldeby.org/blog/index.php/speed-up-your-ubuntu-linux-boot.html](http://aldeby.org/blog/index.php/speed-up-your-ubuntu-linux-boot.html) ' didn't help in explaining that.

---

### Post by Predator106 on 2008-09-20
Bump :)

---

### Post by cariboo on 2008-09-20
If you are not sure waht you are looking at, for instance it looks like kthread is taking a long time to load. Look up kthread in google and see what it does, and if you can stop it from loading. I would suggest not trying to stop kthread as your system probably won't boot.

Bootchart is a great resource, but it takes some research to figure out what you are looking at, 

Jim

---

### Post by Predator106 on 2008-09-20
Oh okay, thanks.

---

