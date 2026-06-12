---
title: "lsb_release -rd VERSUS dpkg --print-architecture"
date: 2008-10-25
forum: General Help
---

### Post by loveunit on 2008-10-25
Hi, 

I wonder if anyone can help me to understand why / how I have both i386 and i686 architecture - I need to download a package file and figured I'd need i386, but these results from terminal are confusing:

I have a dell inspiron 6000 - laptop.

loveunit@loveunit:~$ lsb_release -rd
Description:	Ubuntu 8.04.1
Release:	8.04
loveunit@loveunit:~$ uname -m
i686
loveunit@loveunit:~$ dpkg --print-architecture
i386
loveunit@loveunit:~$ 

thanks in advance.

---

### Post by tormod on 2009-09-29
> **loveunit said:**
> Hi, 

I wonder if anyone can help me to understand why / how I have both i386 and i686 architecture - I need to download a package file and figured I'd need i386, but these results from terminal are confusing:

I have a dell inspiron 6000 - laptop.

loveunit@loveunit:~$ lsb_release -rd
Description:	Ubuntu 8.04.1
Release:	8.04
loveunit@loveunit:~$ uname -m
i686
loveunit@loveunit:~$ dpkg --print-architecture
i386
loveunit@loveunit:~$ 

thanks in advance.
You are running an i686 kernel (uname) on an i386 installation (dpkg). This is in principle fine, although YMMV. Use i386 software packages in this case.

lsb_release does not say anything about architecture, I don't understand why you brought that up in the topic.

---

