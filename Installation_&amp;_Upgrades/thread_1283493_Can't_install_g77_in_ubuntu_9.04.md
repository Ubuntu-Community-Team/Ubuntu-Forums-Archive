---
title: "Can't install g77 in ubuntu 9.04"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by chamithmalinda on 2009-10-05
I cant install g77 in ubuntu. I tried using synaptic but there wasn't a g77 compiler. Also i manually download and install then following error was occured. Please help me.........

[COLOR=Red][B]Error" Dependency is not satisfiable: gcc-3.4
(=3.4.6-6ubuntu3)[/B][/COLOR]

Help me...............................:confused:

---

### Post by ibuclaw on 2009-10-05
Would g77 be the Fortran 77 compiler?
afaik, they've dropped support for that a while ago.

Try:
```
sudo apt-get install fortran77-compiler
```
Which will install **fort77**.

Regards
Iain

---

### Post by chamithmalinda on 2009-10-05
thanks dude its working...........:P

---

### Post by khdani on 2009-10-23
[http://0x5f.blogspot.com/2009/10/install-g77-in-ubuntu-904-jaunty.html](http://0x5f.blogspot.com/2009/10/install-g77-in-ubuntu-904-jaunty.html)

---

### Post by abhishek1912 on 2010-12-17
@khdani

\m/

Newbie here

Works perfectly well in ubuntu 10.04

---

