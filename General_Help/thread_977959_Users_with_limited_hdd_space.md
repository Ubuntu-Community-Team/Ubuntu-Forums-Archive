---
title: "Users with limited hdd space"
date: 2008-11-10
forum: General Help
---

### Post by gased on 2008-11-10
Hi there :)
My first post and i'm not used in making first post and asking for questions but this is very important for me :)

I wanna make a new user but with limited size to him. I've searched all over the net but didn't found something that satisfies me as i got only one partition (actually 3 but one for boot and one for swap o/s). I forgot to mention that the o/s is installed on a dedicated server and its ubuntu desktop 8.04


So how can a make a new user with limited access to root folders and limited disk space :)

 Thanks in advance

---

### Post by unutbu on 2008-11-10
The control you seek is in the quota package.
Here is a (slightly old) guide on how to use it.
[http://www.tldp.org/HOWTO/Quota.html#toc1](http://www.tldp.org/HOWTO/Quota.html#toc1)

After quota has been installed, you might also find useful documentation in /usr/share/doc/quota, or by typing

```
man quota
man edquota
```
in a terminal window.

Having never used this package, I'm sorry I can't tell you specifically how to set it up, but hopefully this points you in the right direction.

---

