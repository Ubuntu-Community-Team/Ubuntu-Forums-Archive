---
title: "Installer hangs on HP Pavilion 8766C"
date: 2008-08-11
forum: General Help
---

### Post by kahlil88 on 2008-08-11
Trying to install Ubuntu 8.04 on my friend's [HP Pavilion 8766C]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=59903&lang=en&cc=us&docname=bph06164"), but it hangs at a black screen with a blinking cursor in the upper left (after the Ubuntu load screen). I tried safe graphics mode, still has the same problem.

---

### Post by Vivaldi Gloria on 2008-08-11
> **kahlil88 said:**
> Trying to install Ubuntu 8.04 on my friend's [HP Pavilion 8766C]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=59903&lang=en&cc=us&docname=bph06164"), but it hangs at a black screen with a blinking cursor in the upper left (after the Ubuntu load screen). I tried safe graphics mode, still has the same problem.

How much ram does it have?

---

### Post by kahlil88 on 2008-08-11
> **Vivaldi Gloria said:**
> How much ram does it have?

384 MB - it looks like 7.10 will boot, but I'd really like something a bit newer. I have dialup and updates are murder on my soul.

---

### Post by Vivaldi Gloria on 2008-08-11
I don't know anything about that computer but here is a standard list of things to try in your situation:

**1)** Google your computer model and ubuntu. May be there's a fix. Seach launchpad bug reports and ubuntu forums.

**2)** Play with boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

**3)** Try alternate cd.

**4)** Install a cli-only system using the minimal cd:

[http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

And then add a desktop environment. For example:

sudo apt-get install ubuntu-desktop.


I suggest you start with option 3.

If nothing works file a bug report.

---

### Post by kahlil88 on 2008-08-12
I sure feel dumb...turns out the problem was with my disc - it has some scratches and what looks like peanut butter on it. I tried one of my shiny unused discs from Canonical, and now Ubuntu 8.04 is up and running!

---

### Post by Vivaldi Gloria on 2008-08-12
> **kahlil88 said:**
> I sure feel dumb...turns out the problem was with my disc - it has some scratches and what looks like peanut butter on it. I tried one of my shiny unused discs from Canonical, and now Ubuntu 8.04 is up and running!

Ha ha ha. Good to hear that. :-)

---

