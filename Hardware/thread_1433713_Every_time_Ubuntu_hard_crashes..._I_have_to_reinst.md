---
title: "Every time Ubuntu hard crashes... I have to reinstall."
date: 2010-03-19
forum: Hardware
---

### Post by nonedrinkwater on 2010-03-19
when I hard boot ubuntu with the power button isntead of shutting it down or sending a kill signal to everything, i get this weird prompt sh:whatever> 

anyways... how do i fix this? or do i have to reinstall???!?!

---

### Post by oldfred on 2010-03-19
The obvious do not shutdown with the power switch. It is never recommended for any operating system as it can cause corruption.

What version of Ubuntu. 

Solutions to many boot issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

---

### Post by nonedrinkwater on 2010-03-19
the newest. 
 9.10

i use wubi to install. 

im thinking about switching distros..... 

gentoo never crashes... wtf.

---

### Post by blur xc on 2010-03-19
> **nonedrinkwater said:**
> the newest. 
 9.10

i use wubi to install. 

im thinking about switching distros..... 

gentoo never crashes... wtf.

I wonder - what are you doing that requires you to do a hard shutdown of your computer?  

BM

---

### Post by oldfred on 2010-03-19
If you are running wubi you do not have a full dual boot install to a separate partition.

The link I gave you has the fix. For wubi see this link from that page:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by nonedrinkwater on 2010-04-01
well that doesnt make sense. 

the whole point of me using this OS was the ease of use factor. 

im switching back to gentoo.

---

### Post by oldfred on 2010-04-01
I am not sure it was a fair comparison. The wubi install is a full install but  as a file inside the windows partition using the windows boot loader to start. It then can be uninstalled from windows. It is meant as a easy for windows users to test and try out without having to repartition the computer and allowing updates that the the liveCD does not.

Gentoo will be a full install and requires a certain amount of configuration.

But the great thing about all linux is we can try many versions for only the cost of time and learning and a little hard disk space. Different versions are there as many of us like different things.

---

### Post by nonedrinkwater on 2010-04-13
if wubi is intended for test purposes then shouldnt it say "for testing only"

---

