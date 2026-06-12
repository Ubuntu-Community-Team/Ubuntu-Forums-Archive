---
title: "Upgrade Old Feisty Server from the Command Line"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by cfiles on 2009-03-06
Has anybody managed (recently) to upgrade an old release to the latest? If so how did you go about it?

I have inherited a server that has feisty installed and it needs to be upgraded. The kicker is I do not have physical access to the server. I have been using do-release-upgrade from the command line and it is failing because it cannot get the upgrade prerequisites. Specifically "Getting upgrade prerequisites failed". Any ideas?

---

### Post by taurus on 2009-03-06
Since feisty has expired and no longer supported, the repos have been moved too.  Therefore, you need to edit /etc/apt/sources.list and replace the current repos (something like **deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)**) to the new one.

```
deb http://old-releases.ubuntu.com/ubuntu/
```

---

### Post by avtolle on 2009-03-06
If you haven't seen [https://help.ubuntu.com/community/GutsyUpgrades#Network%20upgrade%20for%20Ubuntu%20servers%20(recommended](https://help.ubuntu.com/community/GutsyUpgrades#Network%20upgrade%20for%20Ubuntu%20servers%20(recommended)) please take a look at it, which hopefully will be of help.

---

### Post by cfiles on 2009-03-06
I looked at what you guys sent and I was able to get Feisty up-to-date. However, the do-release-upgrade keeps failing. My guess is because it is looking for the Gusty packages at [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-*](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-*)

Is there anyway to make it look in the main archive? Do I need to change the sources back to "archive" instead of "old-release"?

---

### Post by avtolle on 2009-03-06
Yes; you will need to change the /etc/apt/sources.list file to reflect archive rather than old sources. IIRC, there is a discussion in the link I posted which refers to commenting out the "old" Feisty sources, then opening another virtual terminal at some point, removing the commenting, and proceeding. Take a look at that again to see if I recall what I think I do. :)

---

### Post by taurus on 2009-03-06
Yes, change it back to what it was but with gutsy now instead of feisty.

---

### Post by cfiles on 2009-03-06
So it should look like this?:

```
deb http://archive.ubuntu.com/ubuntu/ gusty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-backports main/debian-installer
deb-src http://archive.ubuntu.com/ubuntu/ gusty-backports main restricted universe multiverse
```

---

### Post by taurus on 2009-03-06
> **cfiles said:**
> So it should look like this?:

```
deb http://archive.ubuntu.com/ubuntu/ gusty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gusty-backports **[COLOR="Red"]main/debian-installer[/COLOR]**
deb-src http://archive.ubuntu.com/ubuntu/ gusty-backports main restricted universe multiverse
```

:confused:

---

### Post by cfiles on 2009-03-06
That was in the upgrade guide...

[https://help.ubuntu.com/community/GutsyUpgrades#Network%20upgrade%20for%20Ubuntu%20servers%20(recommended](https://help.ubuntu.com/community/GutsyUpgrades#Network%20upgrade%20for%20Ubuntu%20servers%20(recommended)

---

### Post by cfiles on 2009-03-06
After the change the command is still failing, any other ideas?

---

### Post by avtolle on 2009-03-06
Did you install update-manager-core as instructed in the link prior to running the do-release-upgrade command?

---

### Post by cfiles on 2009-03-06
Yes. The do-release-upgrade command is part of that package.

---

### Post by avtolle on 2009-03-06
Thanks for the information (never had a server to upgrade, so I'm not familiar with the process). What I wonder (that's all this is, wondering) is whether the change of the sources.list to point to old releases is what is fouling things up for you. Reasoning: the somewhat vague comments about just commenting out the extant sources in the list and then removing the comments when reaching a certain step make sense, but **nothing**said about the old releases additions to the file needed to totally update Feisty. In other words, should the additions to the sources.list be commented out when uncommenting the previously existing mirrors as set out in the link.

Just went back to the linked piece (first time I've looked at it in any detail recently) and see where a note has been added indicating that a network upgrade is not possible any more with 7.04; wonder when that was added? Also, I took a quick look at the bug report linked there, and bluntly, something is happening which I don't pretend to understand when reading through the various posts.

---

### Post by cfiles on 2009-03-06
> **avtolle said:**
> but **nothing**said about the old releases additions to the file needed to totally update Feisty. In other words, should the additions to the sources.list be commented out when uncommenting the previously existing mirrors as set out in the link.

I know, that has me curious too.

> **avtolle said:**
> see where a note has been added indicating that a network upgrade is not possible any more with 7.04; wonder when that was added? Also, I took a quick look at the bug report linked there, and bluntly, something is happening which I don't pretend to understand when reading through the various posts.

I do not understand it either :) I may see if I can get somebody on site to do an upgrade off of a CD. I may just be stuck with an old version until we can take this one off line. Thanks for the help!

---

