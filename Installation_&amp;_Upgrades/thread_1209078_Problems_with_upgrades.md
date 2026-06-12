---
title: "Problems with upgrades"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by JordanMobius on 2009-07-09
Whenever I try update or install a new package using apt-get or Synaptic, the things not working properly.  I had always messages like that : 

Reading package list : Done
Building dependence tree
Reading state information... Ready 
E: Impossible find package <package name>

I've tried update the repositories setting but doesn't work.

Somebody could help me !

Thanks.

---

### Post by earthpigg on 2009-07-09
hi jordanmobius,

can you please show us the **_exact_** message or messages it gives you?

thanks.

---

### Post by drs305 on 2009-07-09
Welcome to Ubuntu and the Ubuntu forums.

In addition to what earthpigg requested, please post your /etc/apt/sources.list

```

cat /etc/apt/sources.list  # to display contents
*or*
gksudo gedit /etc/apt/sources.list  # if want to edit

```

---

