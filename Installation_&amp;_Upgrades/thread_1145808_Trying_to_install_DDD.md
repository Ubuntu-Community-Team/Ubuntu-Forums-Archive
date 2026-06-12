---
title: "Trying to install DDD"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by cdietschrun on 2009-05-02
This is on a fresh install of 9.04. I am trying to install DDD for my GDB and the first thing it wanted was lessTif to get installed so I download that and try to install it and it errs on:

configure: error: The development package of the X Window System is required to compiler LessTif, must be at least X11r5.

I went and found [http://xorg.freedesktop.org/releases/X11R7.4/src/everything/](http://xorg.freedesktop.org/releases/X11R7.4/src/everything/) and another site to install, but can't make heads or tails from all that it wants me to install.

The reason I am trying to install lessTif is because the configure for DDD gives me this error: Cannot find termcap compatible library.

I have extracted all my .tar.gz files to my desktop so from my terminal it is ~/Desktop/ddd-3.3.12 or lesstif-0.95.0.

Can anyone help?

---

### Post by Partyboi2 on 2009-05-02
Hi, looks like ddd is in the ubuntu repo's, you should be able to search synaptic for it or install from the terminal with
```
sudo apt-get install ddd
```
If you still need to compile it for some reason you should be able to pull in all the required packages by
```
sudo apt-get build-dep ddd
```

---

