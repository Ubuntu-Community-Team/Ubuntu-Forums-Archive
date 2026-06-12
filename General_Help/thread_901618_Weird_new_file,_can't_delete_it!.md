---
title: "Weird new file, can't delete it!"
date: 2008-08-26
forum: General Help
---

### Post by gkaragoulis on 2008-08-26
One day I went to my /mnt directory to look at my external hard drive mounts, and I saw this crazy new file that I never created.  Officially, the name of the file is "?@?@@?n?@8?@" but I have a feeling that it's completely bogus.  Anyways, I can't delete it, because I don't know what it's called!  I try doing "rm " and then tabbing it to try and make it recognize this crazy file but I can't get it.  Any ideas where this came from or how to delete it?

Also, it's owned by root:root, if that means anything to anyone.

---

### Post by Alaric on 2008-08-26
try this 

```
sudo rm *n*8*
```

---

### Post by raphaelr on 2008-08-26
Or put the name in single quotes.

---

### Post by Vivaldi Gloria on 2008-08-26
> **Alaric said:**
> try this 

```
sudo rm *n*8*
```

In these situations it is better to use the "-i" flag:

```
rm -i *
rm -i *8*
```

Otherwise you can delete other files.

---

