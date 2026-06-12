---
title: "Cleaning repo lists"
date: 2008-09-16
forum: General Help
---

### Post by CyberCowboy on 2008-09-16
Hey all, as I learn more about the way Ubuntu works I'm wondering if there is a way to generate a list of all the packages on my system and which repo they were pulled from, and then remove any repos that I don't have any packages from.

Here's what generates this question, I've inherited a system that is mission critical and the previous admin seems to have thrown repo lists at it just because he found an extra repo, not that he needed any of the software on it.  This sends chills down my spine since I don't know what half these repos are, but the machine does have non-standard software on it.

This machine can't be taken down long enough for me to do a re-install and track down where all the needed software came from so I'm hoping I can at least pull out the repos that aren't in use and maybe generate a list of which packages came from where.

---

### Post by rraj.be on 2008-09-16
```
 sudo dpkg --get-selections >~/Desktop/package-list

Or

 apt-cache pkgnames


```

try man apt-cache or apt-cache for motre options.


But i think there is no command to know the source repo.

You can use synaptic to find the repo source of any package.

---

