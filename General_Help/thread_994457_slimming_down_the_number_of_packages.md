---
title: "slimming down the number of packages"
date: 2008-11-26
forum: General Help
---

### Post by anonymous_user on 2008-11-26
Is there any tips on slimming down xubuntu?

P.S. disk space is not a problem I just want to slim down my OS if possible.

---

### Post by anonymous_user on 2008-12-07
Any advice on this at all?

---

### Post by unutbu on 2008-12-07
These guides are not xubuntu-specific, but maybe they will help you:

How to clean up junk files: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
How to remove unnecessary packages: [http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)
How to empty trash: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

You might also benefit from running
```
gksu baobab
```
Baobab (Disk Usage Analyzer) will make it apparent which directories are taking up the most space.

Finally, go to Synaptic. Click on the Status button. Then click on "Installed". This will show you all the packages on your system. Click on a package and you will see a description. Go through them one by one and remove the ones you don't need.

Keep a list of what you've deleted, and don't delete too many at once. That way, if you later discover you needed a package, it won't be too hard to track down which one to reinstall.

---

