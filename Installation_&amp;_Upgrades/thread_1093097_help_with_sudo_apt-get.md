---
title: "help with sudo apt-get"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by psiho333 on 2009-03-11
Hi!

I have a problem using sudo apt-get [whatever].

For example, when i try sudo apt-get install g++, or sudo aptitude install build-essential, which should be used to install a C++ compiler, I get the same error. No packages found. I have installed ubuntu using wubi (inside windows vista). So perhaps that is causing the problem? And how can I solve it?

thanks for the answer

---

### Post by klemens on 2009-03-11
can you post:

```
cat /etc/apt/sources.list
```

---

### Post by stumbleUpon on 2009-03-11
update your package list and try again. in a terminal

sudo apt-get update && sudo apt-get install g++ build-essential

---

### Post by skymera on 2009-03-11
Sync your sources with the servers.

```
 sudo apt-get update 
```

then install your program

---

### Post by loucifer87 on 2009-03-11
That was my first problem. i just switched to ubuntu herdy few hours ago..
Reading alot of threads here keeps a newbies like me to get a little knowledge about linux.
Thanks guys.. :p

---

### Post by psiho333 on 2009-03-12
thank you very much. It finally works now:D just had to update the list of servers.

---

