---
title: "Making stuff in the right places"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by sshaikh on 2009-04-11
Hi,

If I make things by downloading source (something I believe is common with Linux), I find that binaries are placed in /usr/local/lib.

However when I try to make further things which need these libraries, they expect them in /usr/lib.

Apparently I can change LD_LIBRARY_PATH, but Google says that bad things will happen if I do that. I've resorted to copying the built files to /user/lib, but that hardly seems like the right thing to do (unless it is). Most of the time I'm not even sure if I'm copying the right files!

Is there a "proper" way of dealing with this issue? It happens each time I try to make stuff, but right now I'm asking with reference to memcached and libevent.

---

### Post by Keith Hedger on 2009-04-11
The /usr/lib and /usr/local/lib folders are for library's so you may have to run ```
sudo ldconfig
```
to update your system, you can also force libs to go to /usr/lib by adding the prefix command to configure ie```
./configure --prefix=/usr/lib
```

but you shouldn't really need to do this.
Also check any installation instructions that come with the source code.

---

### Post by sshaikh on 2009-04-11
> **Keith Hedger said:**
> The /usr/lib and /usr/local/lib folders are for library's so you may have to run ```
sudo ldconfig
```
to update your system, 

This worked perfectly. Thanks!

---

### Post by Keith Hedger on 2009-04-12
Don't forget to mark the thread as 'SOLVED'

---

