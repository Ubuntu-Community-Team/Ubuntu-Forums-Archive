---
title: "[SOLVED] Request: deb from source"
date: 2008-09-26
forum: General Help
---

### Post by Aero-Z on 2008-09-26
Hello again,

I'm not very familiar with creating deb-s from source. But if it's easy then could anybody make a i386 deb out of this program please?

[http://gtkevemon.battleclinic.com/]("http://gtkevemon.battleclinic.com/")

Thanks :)

---

### Post by Pro-reason on 2008-09-26
> **Aero-Z said:**
> Hello again,

I'm not very familiar with creating deb-s from source. But if it's easy then could anybody make a i386 deb out of this program please?

[http://gtkevemon.battleclinic.com/]("http://gtkevemon.battleclinic.com/")

Thanks :)
On [http://gtkevemon.battleclinic.com/download.html](http://gtkevemon.battleclinic.com/download.html) there is a [link to a DEB](http://gtkevemon.battleclinic.com/releases/gtkevemon_1.0-1_i386.deb).

You will, however, have to obtain &#8220;libcairomm-1.0-1 (>= 1.6.0)&#8221; before installing it.

---

### Post by cariboo on 2008-09-26
Here is a howto about creating a.deb using checkinstall:

[http://www.falkotimme.com/howtos/checkinstall/index.php](http://www.falkotimme.com/howtos/checkinstall/index.php)

Jim

---

### Post by Aero-Z on 2008-09-26
> **Pro-reason said:**
> On [http://gtkevemon.battleclinic.com/download.html](http://gtkevemon.battleclinic.com/download.html) there is a [link to a DEB](http://gtkevemon.battleclinic.com/releases/gtkevemon_1.0-1_i386.deb).

You will, however, have to obtain &#8220;libcairomm-1.0-1 (>= 1.6.0)&#8221; before installing it.
Yup, there's a deb but it's outdated.
I'm gonna try to make a deb myself =)

---

### Post by Aero-Z on 2008-09-26
> **Aero-Z said:**
> Yup, there's a deb but it's outdated.
I'm gonna try to make a deb myself =)
OK, I got an error now.
```
========================= Installation results ===========================
mkdir -p /usr/local/bin
cp src/gtkevemon /usr/local/bin
cp: cannot stat `src/gtkevemon': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
There's a gtkevemon.cc file in that directory.
Any ideas?

---

### Post by Pro-reason on 2008-09-26
I've just tried to compile the program from the latest SVN revision (no. 58), and it fails.  It's likely to fail for you too.

I downloaded the latest static binary, and it works fine.  You could make a .deb of that binary if you really wanted to, but you could also just move it to /usr/local/bin, which is much simpler.

---

### Post by Aero-Z on 2008-09-26
> **Pro-reason said:**
> I've just tried to compile the program from the latest SVN revision (no. 58), and it fails.  It's likely to fail for you too.

I downloaded the latest static binary, and it works fine.  You could make a .deb of that binary if you really wanted to, but you could also just move it to /usr/local/bin, which is much simpler.
Ok. I'm running the program from the binary at the moment. Just thought to get a clean nice deb package to install and uninstall it.

---

