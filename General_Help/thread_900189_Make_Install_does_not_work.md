---
title: "Make Install does not work"
date: 2008-08-25
forum: General Help
---

### Post by cwhummel on 2008-08-25
I'm not a total noob, but I'm still learning linux. I have looked through countless threads and all over the web, and I can't seem to get this problem figured out.

Ever since I installed linux on my laptop, I have never been able to install an application from a tar.gz file. I run the configure file, but after that the "make" and "make install" never works. It always returns "make: *** No targets specified and no makefile found.  Stop."

I do have "build-essential" installed, and I'm not really sure what else to do. Any help would be great.

---

### Post by jespdj on 2008-08-25
You have to be in the directory that contains the Makefile for this to work, and the author of the software has to have things set up so that this works. If the project is set up properly, the steps are usually:

```
tar xfz filename.tar.gz
cd directoryname
./configure
make
sudo make install
```

What software specifically are you trying to compile and install?

It's only very rare that you have to compile and install software manually this way. For installing software on Ubuntu, you should prefer using the package management system (Synaptic), because it automatically installs libraries that the software needs and makes it easy to uninstall it later.

If a specific piece of software isn't available in the repository, look first if there's a precompiled binary available somewhere, preferrably a .deb package: have a look on [getdeb.net](http://www.getdeb.net/).

Only if there is really no package or binary available, it's time to start trying to compile software from sources.

---

### Post by cwhummel on 2008-08-25
I'm currently trying to install Aurora GTK Engine (i want that snazzy dust theme on digg yesterday). 

I've used that same code before, and retried it just now, and I still get the same result. I usually always go through synaptic first, but I couldn't find it in there.

---

