---
title: "Problem upgrading kubuntu 8.04 to 9.~"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by Nereous5 on 2009-04-11
Hello,
after upgrading kubuntu 8.04 to 9.~ using adept manager....I restarted my system and now it wont even get to the login page....where I input my password....it will get me to the konsole where I get stuck. 
I want to recover Ubuntu and kubuntu since I had both running before just fine....
I tried:
sudo apt-get install kdm
sudo apt-get install --reinstall kdm
sudo apt-get install kubuntu-desktop
and its variant but no luck....anybody has an idea

thanks...

---

### Post by cariboo on 2009-04-11
You can't update directly from Hardy to Jaunty, you have to do it in steps 8.04-->8.10-->9.04. Unfortunately there is no direct update path. I would suggest you use the LiveCD to backup your important files and do a clean install. I don't like to recommend a reinstall, but in this case you are going to have to.

Jim

---

