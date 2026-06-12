---
title: "Does my system support KDE 4.1.3?"
date: 2008-11-26
forum: General Help
---

### Post by diwas on 2008-11-26
My system spec is in my signature...
I have just installed Intrepid (GNOME). And i wanted to install KDE 4.1.3 but ADD/Remove says that it cannot be installed in my system.

I had KDE 4.0 running smooth...in hardy.

So, can I conclude that KDE 4.1.3 cannot be installed in my "primitive" PC?

Thanks.

---

### Post by blazemore on 2008-11-26
That's strange. Have you got a screenshot of it not letting you? .1 is a bugfix, with few new features.

---

### Post by SanskritFritz on 2008-11-26
If you want to install KDE over Gnome, try this:
[http://www.howtogeek.com/howto/ubuntu/install-kde-kubuntu-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-kde-kubuntu-on-ubuntu/)
Otherwise I recommend a fresh Kubuntu install.

---

### Post by diwas on 2008-11-26
> **blazemore said:**
> That's strange. Have you got a screenshot of it not letting you? .1 is a bugfix, with few new features.

Here's the screenshot...

And the link seems to be broken im afraid.

---

### Post by SanskritFritz on 2008-11-27
You should install the package *kubuntu-desktop*, not *kde*.

---

### Post by Xiong Chiamiov on 2008-11-27
> **SanskritFritz said:**
> You should install the package *kubuntu-desktop*, not *kde*.
Kubuntu-desktop installs everything that comes with Kubuntu, while kde installs mostly just KDE stuff, and kde-core installs the bare minimum to run KDE.  I'd suggest the last one, myself, since you've probably already got a PIM, archive manager, photo viewer, etc.

diwas:
64-bit?  SPARC?  Anything unusual?  What about if you run
```

sudo aptitude install kde

```

---

### Post by diwas on 2008-11-27
No, nothing unusual...32 bit simple PC. Hehe

Im very much facinated by plasma and stuffs of KDE...so if i install kde-core will i get them??? 

And why does the ADD/REMOVE say that i cannot install KDE4 Desktop Environment??

---

### Post by diwas on 2008-11-29
I have installed KDE 4.1 (kde-core) over GNOME from synaptic. But I dont think the default plasma are not installed...for instance folder view. So how do i install all the default plasma in KDE??

---

