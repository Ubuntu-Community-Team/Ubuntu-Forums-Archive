---
title: "Installation vs an Upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by gordon33 on 2009-11-08
Hello All

I want to Upgrade to 9.04 then to 9.10 Ubuntu.  Where do I go to get the 2 Upgrades?  Will I have to click on something special for an Upgrade vs a complet install?

I have saved all that needed to be saved from my Ubuntu 8.04m OS.

Gordon webb

---

### Post by raymondh on 2009-11-08
> **gordon33 said:**
> Hello All

I want to Upgrade to 9.04 then to 9.10 Ubuntu.  Where do I go to get the 2 Upgrades?  Will I have to click on something special for an Upgrade vs a complet install?

I have saved all that needed to be saved from my Ubuntu 8.04m OS.

Gordon webb

Gordon,

On software sources (system > administration), and in the update tab, make sure it is set to update to newer releases.  If you do plan to upgrade through the network form hardy 8.04, you have to go sequentially (8.10 > 9.04 > 9.10) and make sure you are updated on each version before proceeding to the next.

Depending on your patience and download speed, it is often better to do a straight install of your preferred version.  Of course, try out the liveCD (live session) first.

Post back if you need a guide to do a manual, fresh install.  Of course, it'll help the forum if you can post as well a gparted screenshot of your HD.

Good luck.

---

### Post by wojox on 2009-11-08
Yes try it out first and try and do a fresh install to get the full advantage of Ext4 and Grub2.

---

### Post by gordon33 on 2009-11-08
Hello Raymond Henson

Thank you for the information.  When I follow the instructions "(system > administration), and in the update tab, make sure it is set to update to newer releases."  

I get lost at "in the update tab" _Update Manager_ is as close as I see in Administration.  Still, clicking on Update Manager I get a box (with out tabs to set to update to newer releases).


Gordon33

---

### Post by raymondh on 2009-11-08
> **gordon33 said:**
> Hello Raymond Henson

Thank you for the information.  When I follow the instructions "(system > administration), and in the update tab, make sure it is set to update to newer releases."  

I get lost at "in the update tab" _Update Manager_ is as close as I see in Administration.  Still, clicking on Update Manager I get a box (with out tabs to set to update to newer releases).


Gordon33


Sorry, meant NORMAL release

system > administration > software sources > updates (tab) > release upgrade > choose normal release

By default, 8.04 will not offer a upgrade to 8.10 because hardy is a LTS version whilst intrepid is a normal release.  When you have set your software sources, access update manager and update.  Once updated, you will be given a window offering you to upgrade to 8.10.  make sure you are updated in 8.04 first before proceeding to intrepid.

[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html)

Good luck.

---

