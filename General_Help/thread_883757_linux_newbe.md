---
title: "linux newbe"
date: 2008-08-08
forum: General Help
---

### Post by rotem30010 on 2008-08-08
hi,
i just installed ubuntu and when i tried to compuile a simple C program with GCC i got the message that stdio.h is not found so no object file was created.
what is the meaning of this and how can i handle it.
thanks.

---

### Post by ilrudie on 2008-08-08
It means gcc can't find the header file it needs.  You probably need to install build-essential.

```
sudo apt-get install build-essential
```

---

### Post by Sycron on 2008-08-08
Post your source if doesn't work..

---

