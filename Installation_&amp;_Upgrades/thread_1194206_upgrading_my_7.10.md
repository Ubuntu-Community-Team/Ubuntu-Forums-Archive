---
title: "upgrading my 7.10"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2009-06-22
I have a system that is running 7.10 and i would like to upgrade it.But i read in a book that using  command
sudo apt-get install dist-upgrade

is not a good way to upgrade a system 
But even with that i realised that there is no longer support for 7.10 because it is over 1.5 yrs
I dont want start installing all application that i installed on it again.

What can i do about this problem?

---

### Post by raymondh on 2009-06-22
Hello 10ghost,

From the upgrade notes :

*End-of-life releases have been supported previously but have reached the end of their support cycle. **It would be best for users of these versions to perform a fresh install of the latest Ubuntu release.** Links have been removed since the upgrades between these versions are no longer supported. However, users still trying to do an upgrade on an experimental basis may find suggestions in: [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184). Upgrading from an EOL to EOL to a supported version is documented here: EOLUpgrades.* 

Here is the link for reference

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

If you scan the forum, the results from network upgrading are mixed (at best).  I am one of those that prefer to do a clean install everytime hence have used HOW-TO's such as

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

in order to keep my settings and tweaks intact.  Lately, I have also created separate /data partitions as I dual-boot.

- Back up your files, 
- download and burn to CD the version you wish to use (to get it ready, just in case), 
- try a dist-upgrade in sequential order  (but as the notes say, it'll be an *experiment*)
- If that does not work for you, consider a fresh install using the liveCD you just downloaded.  That way, you can also set the partitions to your liking.

Good luck and Happy Ubuntu-ing.

---

