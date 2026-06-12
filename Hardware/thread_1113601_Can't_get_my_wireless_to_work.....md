---
title: "Can't get my wireless to work...."
date: 2009-04-01
forum: Hardware
---

### Post by markus789456 on 2009-04-01
It says my wireless card is dectected and working but, i cannot get wireless internet? and i have the newest Ubuntu.

my laptop is a Hp Pavilion dv6000 it has a Aetheos(sp?) wifi chip for a/b/g.

How do you think i could fix this, i'm fairly new to linux so yeah

---

### Post by Dark_Stang on 2009-04-02
Could you post the output of "lspci" for us?

---

### Post by coffeeaddict22 on 2009-04-02
Hi Markus,
Welcome to Linux.
Your post could do with a bit more information.  If you open a terminal (in the Applications/Accessories menu), you'll be able to find a bit more about the problem.  

It sounds like you're happy you've got a network connection.  If so, try ```
route -n
```
which should tell you about the network you're on.

If you don't get anything from that, try ```
ifconfig
```
and post the result of that back here.

---

