---
title: "Install software for release x in release y"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by Andysan on 2009-07-14
Hi,

A simple question, but one that i can't find the answer to; if i want to install a particular application and it's only available for Ubuntu release 'y' (a later version than my version, version 'x') can i do so or will the universe fold in on itself (or equally bad, will stuff not work properly on my PC)?

Thanks!

---

### Post by ptn107 on 2009-07-14
It depends on the program.  I've taken various Karmic pre-release packages and installed them in 9.04, 8.10, 8.04.2 without problems.  You will usually be cautioned by apt-get or aptitude when installing packages that conflict or break others.  Just to warn you now if something goes wrong, downgrading is a pain [when it's even possible] and usually results in a clean install anyway.  Upgrade the software only if you need the new features it provides.

---

### Post by Andysan on 2009-07-14
Thanks, that's a useful reply.  I guess i'll be upgrading my ancient 8.04 boxes then!):P

---

### Post by a7ndrew on 2009-07-28
Just to check, would the syntax in apt-get be:
```
 sudo apt-get install -t karmic foo 
```

to upgrade from foo version x which is on the jaunty repository to some later version which is in the karmic repository?

---

### Post by a7ndrew on 2009-07-31
This syntax doesn't seem to be working... would anyone be able to set me straight? The package I'm trying to upgrade is subversion.

---

