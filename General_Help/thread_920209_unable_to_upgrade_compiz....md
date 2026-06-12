---
title: "unable to upgrade compiz..."
date: 2008-09-15
forum: General Help
---

### Post by yogen on 2008-09-15
hello guys..i have compix 0.7.4...and i want to use the wallpaper feature which is avaialble in 0.7.6...

i have tried various ways...but i'm unable to upgrade my compiz manager...

even tried this...[https://edge.launchpad.net/~compiz/+archive](https://edge.launchpad.net/~compiz/+archive)
but in vain...

help needed...!!!

---

### Post by amedac on 2008-09-15
First, remove compiz completely. Then open terminal and enter this:
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
./compiz-git install
```
(not one line at the time, just copy/paste this in terminal. This will install compiz from git repository. New effects will show up in few hours, maybe one day. I don't know why, but new effect will just appear after some time. You will have Desktop effect, Cube deformation, Atlantis, etc.

---

### Post by yogen on 2008-09-16
> **amedac said:**
> First, remove compiz completely. Then open terminal and enter this:
```
wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz
tar xzf compiz-git-newest.tar.gz
cd compiz-git
./compiz-git install
```
(not one line at the time, just copy/paste this in terminal. This will install compiz from git repository. New effects will show up in few hours, maybe one day. I don't know why, but new effect will just appear after some time. You will have Desktop effect, Cube deformation, Atlantis, etc.
i had done this before...but even after half an hour...is still displayed pulling compiz from git...so i aborted...it had got stuck(not hanged)...!!!

---

### Post by billgoldberg on 2008-09-16
Did you pick the hardy heron repo?

--

Any way, I have an article about it on my blog, take a look and see if that will work.

[http://linuxowns.wordpress.com/2008/07/09/update-compiz-fusion/](http://linuxowns.wordpress.com/2008/07/09/update-compiz-fusion/)

--

Then, after it's installed, read this (second part) to get the wallpaper plugin working.

[http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/](http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/)

---

### Post by yogen on 2008-09-16
> **billgoldberg said:**
> Did you pick the hardy heron repo?

--

Any way, I have an article about it on my blog, take a look and see if that will work.

[http://linuxowns.wordpress.com/2008/07/09/update-compiz-fusion/](http://linuxowns.wordpress.com/2008/07/09/update-compiz-fusion/)

--

Then, after it's installed, read this (second part) to get the wallpaper plugin working.

[http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/](http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/)
i hav done it...but still no luck...
so yesterday night i got fed up...and thought untill i get some solution...i'll use 0.7.4...but now i dont know what the hell has happened...even the 0.7.4 isnt working...im really surprised...it was all good till yesterday evening...at night whenever i tried changing any effect...i got no response...!!!

none of the option is working...even my default animation is disabled...!!!

---

