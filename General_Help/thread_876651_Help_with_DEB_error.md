---
title: "Help with DEB error"
date: 2008-08-01
forum: General Help
---

### Post by Macadeus on 2008-08-01
When I go to run the Synaptic Package Manager i get this error:
E: Type '“deb' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

it says it cant be resolved and wants me to report it to the update-manager

when i try changing the sources.list file it wont let me because i am not the owner, when in reality i am.

---

### Post by ibutho on 2008-08-01
Hi and welcome to the forum.

I suspect there is some sort of error (probably syntax) on line 61 or your /etc/apt/sourses.list file. Can you open it in an editor and post the contents of that line.

---

### Post by Sef on 2008-08-01
> I suspect there is some sort of error (probably syntax) on line 61 or your /etc/apt/sourses.list file. Can you open it in an editor and post the contents of that line.

Applications > Accessories > Terminal

```
gksudo gedit /etc/apt/sources.list
```

Once it opens, then you will be able to comment out line 61.  To comment out a line, put a # in front of it.

---

