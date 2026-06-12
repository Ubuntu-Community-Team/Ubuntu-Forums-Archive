---
title: "error : C can not creat executables. Installing tar.gz"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by rahul_shilps on 2009-05-29
Hi,

I want to do C programs through IDE Anjuta 2.26.2.0. I have downloaded tar.gz of this software.

I also **successfully** extreacted the tar.gz file

Now i have that folder on my home/milind/Documents path

now from terminal, When i give command like : -- > $ sudo  ./configure

It gives me error like : -- >
:
:
checking for gcc... gcc
checking for C compiler default output file name... 
[COLOR=Red]configure: error: in `/home/milind/Documents/anjuta-2.26.2.0':
configure: error: C compiler cannot create executables[/COLOR]
See `config.log' for more details.

---

### Post by Partyboi2 on 2009-05-29
Hi, have you got the build-essential package installed? You can install it with
```
sudo apt-get install build-essential
```

---

### Post by rahul_shilps on 2009-05-30
i fired the command... as u said

the o/p is :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Couldn't find package build-essential[/COLOR]

*What does it mean?*

---

### Post by oldos2er on 2009-05-30
Do you have internet access on this machine? Can you run **sudo apt-get update** before installing build-essential?

---

