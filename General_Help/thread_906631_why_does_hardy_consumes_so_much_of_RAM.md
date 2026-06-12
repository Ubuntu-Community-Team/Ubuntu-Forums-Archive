---
title: "why does hardy consumes so much of RAM????"
date: 2008-08-31
forum: General Help
---

### Post by shredder12 on 2008-08-31
I have installed hardy on my system...
i have 1 gb RAM
 i though it would be enough for running linux on my system..
but thats not so..
if I am running firefox 3 and rhythmbox on my system 800 MB of the RAM is already being consumed..
It's really hard to run a lot of things simultaneously on the system..
even if i m hardly running anything on  my system... 400-500 Mb of the memory is being consumed..
why is that so...??
why does linux consumes so much of RAM..or is it just hardy..??

---

### Post by jerome1232 on 2008-08-31
How are you determining this?

Try looking at free for your amount of free ram
```
free -m
```

look at the row that says "-/+ buffers/cache", the column that says "free", that's free ram.

My system has 1 GB of ram and I've never used more than 512 MB of ram. Compared to my vista machine with 3 GB of ram and uses ~2 GB on average.

---

### Post by shredder12 on 2008-08-31
hey..
thanks...
that buffers/cached displays 683 mb ram to be free.
but then what does the first line means..which says that only 16 mb is free...

---

### Post by jerome1232 on 2008-08-31
Basically ram not used is wasted so linux uses it to cache files hoping they get used again (actually blocks of data not full files)

here's a exerpt from the gentoo wiki that explains it a bit better, it's for gentoo but applies to Ubuntu too.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

