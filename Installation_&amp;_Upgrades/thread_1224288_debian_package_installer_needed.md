---
title: "debian package installer needed"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by roschell on 2009-07-27
I just installed xubuntu through the alternate cd I added synaptic, browser and others but need to get some downloaded packages.

How can I add the package for installing .deb packages which is normally in under the right click button. I have tried some packages but with no success.

Thanks

---

### Post by helix2301 on 2009-07-27
Add / Remove Programs under the ubuntu logo.

---

### Post by ajgreeny on 2009-07-27
Do you mean dpkg?  I had always assumed it was installed by default on all the (*)ubuntu family of distros, but perhaps I'm wrong.  You can add it with synaptic or simply with ```
sudo apt-get install dpkg
```

---

### Post by roschell on 2009-07-28
I have got dpkg installed however it is not under the right click button on offer. It always has been convenient way in installing .deb packages. => still without it.

Or can I somehow add it to the options?

Thanks

---

### Post by ajgreeny on 2009-07-28
I wonder if what you really need is **gdebi** which is almost the graphic version of dpkg.  Get that and you may have exactly what you are looking for.  Search in synaptic for it and see if it helps you.

---

### Post by roschell on 2010-08-31
Thank you, gdebi solved the problem.

---

