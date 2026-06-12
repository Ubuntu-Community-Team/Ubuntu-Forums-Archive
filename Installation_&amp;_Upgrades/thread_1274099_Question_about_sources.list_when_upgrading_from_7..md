---
title: "Question about sources.list when upgrading from 7.04 to 7.10"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by QADude on 2009-09-24
I am trying to upgrade from 7.04 to 7.10, then from 7.10 to 8.04.

I am going by the instructions at this website: 
[https://help.ubuntu.com/community/EOLUpgrades/Feisty](https://help.ubuntu.com/community/EOLUpgrades/Feisty)

The website says:

**Please make sure you have the following sources.list. **

[B]## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse[/B]


Does this mean that the sources.list file should only have these entries?

Or does it mean that these entries should be appended to the sources.list file?

---

### Post by wojox on 2009-09-24
Yes what you have look correct. Now just:

```
sudo aptitude update && sudo aptitude upgrade
```

```
sudo do-release-upgrade
```

---

### Post by mikewhatever on 2009-09-24
I think it doesn't matter whether or not you remove the current lines in the sources.list. Feisty's repositories are long gone, and you'll just get a bunch of error from them. Comment them out if you want, or leave them be.

IMO, what you want to do is achieved easier by backing up and installing 8.04 directly.

---

### Post by theozzlives on 2009-09-24
Feisty and Gutsy both have reached end of life, I'd recommend a fresh install.

---

