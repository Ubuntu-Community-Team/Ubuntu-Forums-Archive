---
title: "[SOLVED] Network Install..."
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by icanfly0307 on 2008-12-24
Hi all,
       I messed up my Ubuntu installation yesterday, so I'm up for a fresh install. I've downloaded and burned the mini CD so that I can install from the internet. However, *us.archives.ubuntu.com *seems to be down or under maintainence because their server is *very* slow. I'm trying to switch mirrors at the selection screen but I can't figure out which keys to press. I've tried a whole bunch that didn't work. Any Suggestions? Thanks. :)

---

### Post by zvacet on 2008-12-24
```
gksudoo gedit /etc/apt/sources.list
```

and replace all  **us.archives.ubuntu.com** with **archives.ubuntu.com**
save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by icanfly0307 on 2008-12-24
Thanks, but how do I access /etc/apt/sources.lst? I formatted my previous ubuntu partition and the fresh installation process crashed in the middle saying that the server was down. Like I said, I'm accessing the Internet Install through the Mini CD from Ubuntu's website.

---

### Post by icanfly0307 on 2008-12-24
Never mind. Got it sorted out. The installer asked me on the first screen about the country that I was in. Changed it and WALA! it worked! Thanks for your time anyway.

---

