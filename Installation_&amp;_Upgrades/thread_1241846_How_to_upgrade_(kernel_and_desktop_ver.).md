---
title: "How to upgrade (kernel and desktop ver.)?"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by SeePU on 2009-08-16
How should one upgrade the kernel and desktop version?  

That is, without breaking the system.   I am used to just installing anew when Ubuntu/Kubuntu moves to the updated version.

Is there some steps of what you need to do (first)?   Can I find some steps posted someplace or can someone help me here?

---

### Post by slakkie on 2009-08-16
Search for upgrades in the wiki.

The easiest way is via the update-manager (GUI). In a terminal type:

```

sudo aptitude update && sudo aptitude safe-upgrade
sudo update-manager

```

The other easy way is via the command line, which is basically the same tool.

```

sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade

```

You may want to look here: 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

