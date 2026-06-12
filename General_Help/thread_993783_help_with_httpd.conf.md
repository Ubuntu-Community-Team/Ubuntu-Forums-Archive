---
title: "help with httpd.conf"
date: 2008-11-26
forum: General Help
---

### Post by firebladeharsha on 2008-11-26
I have been trying to get my SIPp acess external IP`s but I keep getting error from local host at 127.0.0.1

Googling has taught me that httpd.conf has to be edited to allow applications to access external IP`s....but I cant find it on my PC......runs Ubuntu 8.04....

Pls help.

---

### Post by Peter09 on 2008-11-26
type the command below in a terminal to see what your routing is set up to.


```
route -n
```

You should not have to do much on your Ubuntu machine to access an external IP. More likely you have not got your default gateway set up in network manager.

---

