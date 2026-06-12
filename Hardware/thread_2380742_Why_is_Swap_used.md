---
title: "Why is Swap used?"
date: 2017-12-21
forum: Hardware
---

### Post by felldin on 2017-12-21
Hi,
I'm using "free -m" and get the numbers below:

```

              total        used        free      shared  buff/cache   available
Mem:           7983        1284        192          58        6506        6314
Swap:          1019         220        799

```

If i run the command a couple of times i can see that memory used by Swap changes a little bit (pending from 215MB to 230MB). 

Why is the swap used when I got so much Memory available? Is this a problem? Should I consider to upgrade the memory on the computer?

---

### Post by TheFu on 2017-12-21
Not an issue. No need to add more RAM.  System is working as designed.

If this is a desktop, you might want more swap.  For a server, if you carefully monitor the RAM use, it is possible to remove all swap from the system.  Don't do that without a few months of system RAM monitoring. On most computers, when RAM runs out, a system crash happens. That's bad.

---

### Post by Yellow Pasque on 2017-12-21
[https://old.lwn.net/Articles/83588/](https://old.lwn.net/Articles/83588/)

---

