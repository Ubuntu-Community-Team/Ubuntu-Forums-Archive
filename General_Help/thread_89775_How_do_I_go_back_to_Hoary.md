---
title: "How do I go back to Hoary?"
date: 2005-11-13
forum: General Help
---

### Post by add1sun on 2005-11-13
I did a fresh install of Breezy on a new machine and everything is nice except my apps crash randomly.  It is mainly browsers (not just FF, Epiphany too) but I've had jEdit, Thunderbird, and GIMP go down too.  The app just closes out of the blue with no error or anything (nothing in logs).

Anyway, I'm tired of mucking with it.  Is it possible for me to go to Hoary without doing a fresh install again?

---

### Post by aysiu on 2005-11-13
A fresh install isn't as bad as you may think.

I was dumb enough to do an early upgrade to Dapper. After it forcibly removed my mplayer plugins and wouldn't let me reinstall them, I had to reinstall Breezy to get a working system again (no more early upgrades for me--in fact, I won't be going to Dapper probably until June of 2006, two months after its release).

I backed up my important files (everyone says use a separate /home partition, but I like clean installs) and reinstalled. I'd say to reinstall and configure everything again, it took me only about two hours.

---

### Post by Xian on 2005-11-13
[QUOTE=add1sun]Anyway, I'm tired of mucking with it.  Is it possible for me to go to Hoary without doing a fresh install again?[/QUOTE]

You'd need to pin the Hoary repos so that apt will install those packages over the ones from Breezy. Otherwise, it will condisder the Breezy deb files to be preferred based on their version numbers.

Here's a couple of pinning how-to's:

[Apt Preferences & Pinning](http://ccrma.stanford.edu/planetccrma/man/man5/apt_preferences.5.html)
[Apt Pinning in Debian](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

