---
title: "Best way to hack gnome?"
date: 2008-07-16
forum: General Help
---

### Post by monkeyBox on 2008-07-16
There are some thing's I'd like to change about my gnome-desktop, and I want to  the source code.   I used to do this when I used Gentoo, and it was fairly easy because the ebuilds were based on source. Now that I'm using ubuntu, I wonder what the best way is to hack gnome.

For example, I have a patch for nautilus I made awhile back for the ability to lock desktop icons (it's been in gnome bugs for awhile and it doesn't look like they're going to adopt it any time soon),  and I want to apply it.  I don't necessarily want to use the latest bleeding-edge version of gnome, I'd just like to use the stable version.  

What's the "best way" to do this?

---

### Post by r0g on 2008-12-30
I know this is an old thread but I'm wondering the same thing.

---

### Post by heindsight on 2008-12-30
You can download the source from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For example, the source for nautilus on hardy can be downloaded from [http://packages.ubuntu.com/source/hardy-updates/nautilus](http://packages.ubuntu.com/source/hardy-updates/nautilus)

You'd have to download quite a lot of files though: the original source code and ubuntu patches and you'd have to install all the build dependencies.
 
It would probably be easier to enable the source code repositories (System -> Administration -> Software Sources) and then install the source packages using apt-get (have a look at the apt-get man page to see how to do this, I've never done this so I can't really help with that part)

---

### Post by sdennie on 2008-12-30
The basic idea is the following:

```

apt-get source nautilus
sudo apt-get build-dep nautilus
cd nautilus*
dpkg-buildpackage

```

You will then have new packages above the nautilus directory.  You will want to find a more thorough guide than that but, that's the basic idea.

---

