---
title: "Wubi, Instalation Size, Does it matter?"
date: 2008-09-15
forum: General Help
---

### Post by Corporal Nickel on 2008-09-15
a Quick Question (this is my 100 percent Ubuntu Linux Machine)
my sister [Mac user] wants to know does the installation size really matter? it ranges from 4gb to 30gb. she wants to waste as less space as possible but wants to be able to save all her content on it.

Any idea's? is 4gb the size it would reflect on Ubuntu [as a hard drive] Like, if she installs it 4gb she will only have 4gb of space to use? ETC, ETC.

---

### Post by Corporal Nickel on 2008-09-15
Any amount of advice just a quick yes/no to answer me :p?

---

### Post by Corporal Nickel on 2008-09-15
*bump* ;3

---

### Post by Corporal Nickel on 2008-09-15
Final Hope Bump.

---

### Post by MaxIBoy on 2008-09-15
> **Corporal Nickel said:**
> a Quick Question (this is my 100 percent Ubuntu Linux Machine)
my sister [Mac user] wants to know does the installation size really matter? it ranges from 4gb to 30gb. she wants to waste as less space as possible but wants to be able to save all her content on it.

Any idea's? is 4gb the size it would reflect on Ubuntu [as a hard drive] Like, if she installs it 4gb she will only have 4gb of space to use? ETC, ETC.

Basically, Wubi prevents your Ubuntu from seeing, reading, or writing to the host filesystem (as far as I can tell,) so that size is the size of hard drive space that will be visible to and usable by Ubuntu (unless you have another partition, which defeats the point of Wubi anyway.)

---

### Post by Elfy on 2008-09-15
afaik - the host is accessible in /host(s), whether it can share I'm not sure.

But to answer the question - if you give wubi a 4Gb disc that is what you will have available to ubuntu. It is possible to resize it, but I've never done so myself.

This is the wiki for wubi - which covers much - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

It is best to bump only after 24 hours. 3 in less than 30 minutes could anatagonise some ;)

---

### Post by sailor2001 on 2008-09-15
I am using 13g and can't imagine using anymore than that, BUT I don't save music or movies, just pics

---

### Post by meindian523 on 2008-09-15
If you are planning to migrate to a full dual boot(or a pure Ubuntu machine hopefully) later,it wouldn't matter,because then you can use LVPM to migrate your Wubi install,data,passwords and all directly to a partition.I don't have the exact URL,but a Google search would easily yield it.

---

