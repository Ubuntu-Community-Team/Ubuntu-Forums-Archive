---
title: "crontab entries ?"
date: 2008-07-18
forum: General Help
---

### Post by brijith on 2008-07-18
Hai ,

Can we invoke GUI setting as a crontab  entry? What I mean is can we give 

```
22 19 * * * gedit my_fle
``` in crontab? Will it work ??

---

### Post by apswartz on 2008-07-18
Yes, it should work. Give it a try.

---

### Post by hyper_ch on 2008-07-18
it shouldn't work ;)

---

### Post by apswartz on 2008-07-18
> **hyper_ch said:**
> it shouldn't work ;)

Well, I can't argue with that. Perhaps it **shouldn't** work. It seems to be a bad idea.

---

### Post by brijith on 2008-07-18
When I tried It didn't Worked. If I have to do something like this how could I do it. is there any other methods to Do it !

---

### Post by hyper_ch on 2008-07-18
cron runs in a userspace with no x... you ahve to export it to one with x... this issue has been asked a few days ago with a solution.... I also posted in that thread then... so I guess you should be able to find it.

---

### Post by brijith on 2008-07-19
> **hyper_ch said:**
> cron runs in a userspace with no x... you ahve to export it to one with x... this issue has been asked a few days ago with a solution.... I also posted in that thread then... so I guess you should be able to find it.

Thank you Those posts are very informative :)

---

