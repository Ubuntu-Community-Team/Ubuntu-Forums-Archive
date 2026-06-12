---
title: "playing mp3 sudo dpkg"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by jsweeny on 2009-07-08
When I tried to play an mp3 form a website, it told me that there was a plug in missing.  So when prompted I searched for the plug in.  Then it found the plug in to use and to install.  After telling to install, I get a message that it couldn't and I had to do sudo dpkg -a to fix problem.  What does this mean.  How do I listen to mp3 and watch videos on sites like youtube???

---

### Post by spcwingo on 2009-07-08
First, open a terminal and type the command it tells you to.  For everything else, run this command:

```
sudo apt-get install ubuntu-restricted-extras
```

That will pull in Java, Flash, A/V codecs, MS Fonts, etc.

---

### Post by oldos2er on 2009-07-08
> **jsweeny said:**
> When I tried to play an mp3 form a website, it told me that there was a plug in missing.  So when prompted I searched for the plug in.  Then it found the plug in to use and to install.  After telling to install, I get a message that it couldn't and I had to do sudo dpkg -a to fix problem.  What does this mean.  How do I listen to mp3 and watch videos on sites like youtube???

 Did you run **sudo dpkg --configure -a** ? That command fixes packages that weren't installed properly the first time around. Run **man dpkg** for more info.

---

