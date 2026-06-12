---
title: "Re-installing packages"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by grkuntzmd on 2009-10-27
This coming weekend, I, like MANY others, will be upgrading to Karmic Koala with a clean install.

I would like to reinstall SOME of my existing packages, upgrading to the latest version, of course. I don't want to reinstall everything, so I will need to mark the packages I would like to get.

What is the best approach to do this? I would like to somehow dump all of my existing packages and mark the ones I want to reinstall (maybe by editing the list with vi, marking each interesting package with "OK", then using gawk to filter the list).

I would like to automatically install any dependencies that the marked packages require.

What is the best way to accomplish this?

I will be using the x64 distro, so the technique must accommodate "dpkg --force-architecture" for the packages that are only available as x86.

Thanks.

NEVER MIND. I FOUND THE HOW-TO.

---

### Post by zvacet on 2009-10-27
> NEVER MIND. I FOUND THE HOW-TO.

Share it with others with similar question.

---

### Post by grkuntzmd on 2009-10-27
Sorry.

[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

