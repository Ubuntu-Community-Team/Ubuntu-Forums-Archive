---
title: "HELP! Winecfg is spitting out wingdings!!"
date: 2005-11-30
forum: General Help
---

### Post by remick182 on 2005-11-30
I don't know what happened exactly.  I was using wine a couple of days ago and it was fine.  Last night I saw an update available through Update Manager for wine.  I applied the update and went to bed.  Today, I went to run winecfg and make some changes for a program and everything was written in some kinda symbol language w/ a bunch of circles and sqiggles.  What happened?
I tried to remove wine through Synaptic, and then reinstall it, but I still can't read anything.  What's a poor unexperienced Ubuntu user to do?

---

### Post by ltmon on 2005-11-30
1. If you are not already doing so, use the wine version from [http://winehq.org](http://winehq.org).   It's a much newer version, and I found it works better.  There's instructions on that site for installing on Ubuntu.

2. Make sure you have installed the msttcorefonts package also.

Cheers,

L.

---

### Post by remick182 on 2005-12-01
Just curious, but the newest version of Wine listed on their homepage is version **0.9.2** and this is the same version as listed under Synaptic Package Manager.  This is also the same version downloaded and installed via *[COLOR="DeepSkyBlue"]sudo apt-get install wine[/COLOR]*.  Is the version from Wine's site really newer or different?

---

### Post by remick182 on 2005-12-01
It was the msttcorefonts that was causing the problem.  I'm not sure what happened, unless the update to Wine for some reason disabled or deleted the fonts. Oh well, it's working now!  Thanks.

---

