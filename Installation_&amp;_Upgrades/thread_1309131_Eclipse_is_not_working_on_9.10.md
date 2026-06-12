---
title: "Eclipse is not working on 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-11-01
Eclipse is not working on 9.10

I have download eclipse from [www.eclipse.org](www.eclipse.org).
then installed it, but when I try to installed plugin it doesn't work.
Aad site.
name=I give some name
location:http:// plus the link of the plugin
when I click on ok nothing happen.
I have tried also to change the jdk when I click on OK for the final action nothing happen.

---

### Post by julv on 2009-11-01
Hi,

I have the exact same problem with ubuntu 64bits / galileo 64bits too

---

### Post by Kokopelli on 2009-11-01
You need to set the environment variable GDK_NATIVE_WINDOWS=true

I launch eclipse from the command line so added an export in my .bashrc
```
export GDK_NATIVE_WINDOWS=true
```

if you use a menu entry you could probably do
```
export GDK_NATIVE_WINDOWS=true;/path/to/eclipse/eclipse
```

or create a simple bash script to launch instead.

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257](https://bugs.eclipse.org/bugs/show_bug.cgi?id=291257)

---

### Post by julv on 2009-11-01
thanks !

I had found out that pressing the space bar while hovering did the trick though, but it's really a pain...

---

