---
title: "Xorg sluggish on Thinkpad T500"
date: 2009-05-19
forum: Hardware
---

### Post by diagonallemma on 2009-05-19
Hi,

I've just installed Ubuntu 9.04 on a friend's Thinkpad T500 (fresh install), and it looks like Xorg is slowing everything down a lot. For instance, switching between applications with Alt-Tab is painfully slow, and there is a very noticable delay until characters show up when entered in Texmaker. In either case, top shows that Xorg is eating most of the CPU power. This happens whether or not Desktop effects are on. 

Under Administration -> Hardware drivers, Ubuntu suggests to install fglrx drivers, which allegedly have been tested by Ubuntu developers; but when we activated this, the system immediately froze as soon as it entered X Windows, so I had to manually remove the fglrx settings from xorg.conf in recovery mode. All in all, not a very pleasant experience.

Any ideas what is going on here, or what we can do? Should we downgrade to Xorg 1.5?

---

