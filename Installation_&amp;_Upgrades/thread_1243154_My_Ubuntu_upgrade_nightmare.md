---
title: "My Ubuntu upgrade nightmare"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by treehouse on 2009-08-18
My clean install of Jaunty had a seemingly incurable problem ([see this thread for details](http://ubuntuforums.org/showthread.php?t=1240611)) and so I downloaded and did another fresh install of Hardy with the intent to upgrade from that fresh install. I can't get it to upgrade. I have tried 'apt-get dist-upgrade' 'apt-get upgrade' 'update-manager -c' 'update-manager -p'.

---

### Post by slakkie on 2009-08-18
My telepathy skills are not like my Unix skills, so could you please post more details regarding your upgrade?

Ahhhh, maybe I know what your problem is, have a look in the file:

/etc/update-manager/release-upgrades

You need to change something over there and then run the upgrade.. I think that dist-upgrade can upgrade your machine, but you need to make changes to your sources.list. I would advise the update-manager.

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by treehouse on 2009-08-18
Thanks dude. I somehow overlooked the dropdown that was on LTS only instead of 'normal'.

---

