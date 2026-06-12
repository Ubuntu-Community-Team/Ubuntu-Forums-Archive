---
title: "Common developer tools package?"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by Bogdanovist on 2009-03-13
Hi All,

I've been using Linux/Unix for many years, however always at study/work where someone else (sys admin) was looking after the back end of the system (I'm in academia). I recently installed Ubuntu (8.10) on my laptop and this is the first linux installation I've done myself (not that it is hard to install Ubuntu!). 

What I've noticed is that all the (to me) standard tools that I use Linux for don't seem to be installed by default (e.g. emacs, lyx, g++, cmake, latex...). Now, they are very easy to install and the terminal tells you exactly what to even type to get them with the package manager, but I'm finding it a bit annoying to have to keep installing things ad hoc when I go to use them. Lyx is currently installing and is taking a while, I'd prefer not to have to wait around while I'm working. Does anyone know if there is a basic package I can install that contains a range of common developer tools such that these will be installed all in one go (and how to install it)?

Thanks in advance.

---

### Post by lloyd_b on 2009-03-13
AFAIK, no such package exists.  There is the "build-essential" package, which provides everything needed to compile programs, but nothing else beyond that.

I suspect the reason for this is that what you consider to be "standard tools" are a matter of taste.  For instance, should the standard package include "vim" or "emacs"? (be ready for a flame war if you actually try to answer that one...).

You could potentially write a shell script, with a long "sudo apt-get install ..." command that installs all of the packages that you consider to be standard.  Then if/when you move to another machine, you can just run that script and get everything you want installed in one go...

Lloyd B.

---

### Post by Bogdanovist on 2009-03-13
Thanks for the info. I've probably got most of what I need now, I installed build-essential but almost all of it was already done. I'll keep your advice in mind if I need to build a new system sometime.

Cheers.

---

