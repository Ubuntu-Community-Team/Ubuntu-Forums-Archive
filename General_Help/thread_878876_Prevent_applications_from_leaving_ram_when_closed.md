---
title: "Prevent applications from leaving ram when closed"
date: 2008-08-03
forum: General Help
---

### Post by bpl07 on 2008-08-03
Is there a way to prevent applications from leaving ram when I close them?  I have plenty of ram on my system and rarely use more than 25% of it.  I noticed in system monitor that when I close firefox roughly 100 Mb becomes free in ram, which to me means that when I reopen firefox it'll need to reload that 100 Mb.  Is there a way to prevent this besides just minimizing the window of the application?

---

### Post by dexter.deepak on 2008-08-03
thats what happens while hibernating !!your ram contents are copied to hard-disk ; since ram is volatile memory, you cant expect it to have persistent storage.

---

### Post by dexter.deepak on 2008-08-03
i am sorry i didnt bother to read your entire post.
after actually reading it, i guess you should look for ram-disks:
[http://www.design.iastate.edu/LABS/articles/article0017.html](http://www.design.iastate.edu/LABS/articles/article0017.html)

---

### Post by bpl07 on 2008-08-03
> **dexter.deepak said:**
> thats what happens while hibernating !!your ram contents are copied to hard-disk ; since ram is volatile memory, you cant expect it to have persistent storage.

Yeah I know that, but I'm talking about during normal use, not between shutdowns.  I heard OSX does this, and I figured ubuntu should be able to do it also.

---

### Post by sdennie on 2008-08-03
The huge amount of memory that is being released by firefox is likely a combination of things that firefox has created dynamically and memory leaks (the ratio of which can be approximated by the version of firefox you use), neither of which can be preserved between firefox sessions.  There is a good chance that much, if not all, of the parts of firefox that are static (so, read off the disk) are sticking around in memory after you close it.

---

### Post by crazedgremlin on 2008-08-03
While not exactly what you're looking for, this will do the trick.  It keeps files needed to start your most frequently-used programs in your RAM.

[http://en.wikipedia.org/wiki/Preload_(software](http://en.wikipedia.org/wiki/Preload_(software))
```
sudo apt-get install preload
```

---

