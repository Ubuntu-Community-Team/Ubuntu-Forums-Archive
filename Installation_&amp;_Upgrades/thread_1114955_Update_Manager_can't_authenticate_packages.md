---
title: "Update Manager can't authenticate packages"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by alphacrucis2 on 2009-04-03
Running 8.10 and the update notification indicted 36 updates available. However when I attempt to install the updates, update manager gives a warning about many of the packages can't be authenticated. Not sure whether to install or not so I cancelled the update. Any ideas as to what would be causing this?

---

### Post by taurus on 2009-04-03
did you add ppa.launchpad.net's repo to your /etc/apt/sources.list for the latest KDE?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by alphacrucis2 on 2009-04-03
> **taurus said:**
> did you add ppa.launchpad.net's repo to your /etc/apt/sources.list for the latest KDE?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

This one I guess. I can't actually recall what I added that for:

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```

---

### Post by taurus on 2009-04-03
> **alphacrucis2 said:**
> This one I guess. I can't actually recall what I added that for:

```
deb http://ppa.launchpad.net/kubuntu-members-**[COLOR="Blue"]kde4[/COLOR]**/ubuntu intrepid main
```

You want the latest KDE.

Here are a couple of links for you to look at.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

