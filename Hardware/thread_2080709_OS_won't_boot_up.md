---
title: "OS won't boot up"
date: 2012-11-04
forum: Hardware
---

### Post by pAIgn10 on 2012-11-04
Hi there. Very recently I got involved with linux, and since I have no idea what goes around it, I need your help.

I have an HP Pavilion dv6-2120ev, I have installed Xubuntu 12.04 and Windows 8, Xubuntu runs on an SSD.

When I try to boot Xubuntu, most of the times I get a black screen and the caps lock led flashes. Some times I get info like those in the images below. When it happens to actually boot up, everything runs fine (as far as I can tell).
```
https://www.dropbox.com/s/g8bhtv8z8i8p8sf/prob1.jpg
https://www.dropbox.com/s/zhbszheqr6a9eyk/prob2.jpg
```

So, any ideas?

---

### Post by Yellow Pasque on 2012-11-04
The technical term for what you're experiencing is "kernel panic." They're kind of difficult to troubleshoot. The best thing may be using an updated kernel (or Ubuntu 12.10) and see if it's already been fixed in the kernel code.

---

### Post by pAIgn10 on 2012-11-05
OK, thank you very much. I'll look into it.

---

### Post by Yellow Pasque on 2012-11-05
The 3.5.x kernel from Ubuntu Quantal/12.10 is available in the precise-proposed repo.

---

