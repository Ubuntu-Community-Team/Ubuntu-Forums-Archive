---
title: "Apititude on Slackware?"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by snowman4839 on 2009-09-07
I've been looking at messing around with Slackware for the past few days and the overall impression I get from Slackware's default package manager is that.... it sucks. Is there any way that I can use aptitude from Debian or Debian-based Linux OS's or YUM from fedora on Slackware? Since they're all based on the Linux kernel, does that allow them to be interchangeable or does the way they coded the actual OS make them noninterchangeable? If it is the case that they aren't interchangeable, then what makes that so? Thanks

---

### Post by Whiffle on 2009-09-07
It won't work, at least not without tons of work, and even then it would probably be spotty.  You'd have to figure out how to get apt to recognize what is already on the slackware system and use that to check dependencies.  Since slackware packages don't include dependency information and are not compatable with .deb packages, this would be difficult to say the least.

Slackware has a different philosophy from most distros, following the KISS philosophy to the letter.  This makes for a fast, stable distro, but doesn't necessarily make it easy to use.  They have decided that a dependency checking package manager is against that philosophy, and therefore don't have one, and expect the user/administrator to do the work.

If you want a dep checking package manager, and stability, get debian.

---

### Post by oldos2er on 2009-09-07
The closest you can get is slapt-get ([http://en.wikipedia.org/wiki/Slapt-get](http://en.wikipedia.org/wiki/Slapt-get)), but it's still not as functional as apt-get or aptitude.

---

