---
title: "Full juice out of Xeon Quad Core?"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by murmel on 2008-02-12
Hello everybody! A simple question with, maybe, a rather harder answer. How do I get the full juice out of my Xeon Quad Core? In example when running a gamingserver (oa/nexuiz) or benchmarking it (nbech?). I would also like to know how to test my system and see how well it works.
Thank you!

- Simon

---

### Post by Jimmey on 2008-02-12
I think you would need to install a special kernel - I think the SMP kernel has support for more than one core..I might be wrong, though. Open up the Synaptic package manager, and a search for "Linux smp" might return something useful.

I'm sure that I've seen some conky screenshots where each core can be monitored for its load - Do a few searches on the forum to find how to do that.

---

### Post by murmel on 2008-02-12
Haven't really found anything when searching. Probably because I'm searching for the wrong stuff. But it would be great if someone could post some links to places where they write how to use these cores.

---

### Post by murmel on 2008-02-14
I've been reading about this today and have found some intresting stuff. Some about multithreading. And I've also tested alot of programs, wich none of them have been able to use more then one core.
I know that WinRAR is able to benchmark multithreaded. Is there any program that can do the same for linux? Maybe rar itself?

---

### Post by murmel on 2008-02-14
I've just found a program named "pbzip2" wich uses ptreads or what it's called to use all four of my cores. It's really something!
It takes about 2 min to compress 746mb to 723mb. (bz2)
I don't really know how good that is, but it was sweet to see all four of them work together!

---

### Post by murmel on 2008-02-15
Does nobody know nothing about multithreading software for linux? :(

---

### Post by murmel on 2008-02-16
a little bump .. :)

---

### Post by 444 on 2008-02-16
It's an application level thing, whoever made the program has to include support. The Ubuntu kernel already comes set to use upto 8 cores.

Nexuiz looks like it does not support it, while OpenArena looks like it does.

---

### Post by murmel on 2008-02-17
I've noticed the "ioquake3-smp.*", but that's for the client. I'm not using a graphical interface for the server. :/

---

