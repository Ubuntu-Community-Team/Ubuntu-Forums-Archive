---
title: "Formatting 2nd Hard drive"
date: 2008-09-15
forum: General Help
---

### Post by Higatron on 2008-09-15
What's the best app to do this with? And when I do, what's the best format to make my partitions in?

---

### Post by bodhi.zazen on 2008-09-15
Best file system is a matter of opinion.

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

You can format with gparted or from the command line, 

```
mkfs.ext3 /dev/sda1
```

---

### Post by scooterpd on 2008-09-15
if you are already running linux, and this second hdd is just for files or anything other than a windows os, i would use gparted and go for ext3.

---

