---
title: "why package(gammu) in Hardy Heron is not the latest ?"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by mrprajesh on 2009-04-12
i am using Ubuntu 8.04 ,i have installed gammu through terminal
      sudo apt-get install gammu

when i checked the version of gammu installed ... it was 1.18.90. My Ubuntu says it is the recent version of gammu ...but it is not so!

the recent version is 'Gammu stable 1.23.1' ([www.gammu.org](www.gammu.org))

Can anyone explain me why is this difference ? ? ?
why the recent version of gammu is different for various version of Ubuntu (i found this in package.ubuntu.com)

sorry if my english is bad !

---

### Post by hyper_ch on 2009-04-12
packages version != latest trunk

at some time you get a freeze on software updates with regard what ends up into the repositories. From this point on you'll only get bugfixes and security updates but usually version numbers does not increase.

However you can enable proposed and backports updates, that will probably give you newer versions for some stuff.

In addition there are also 3rd party repos that give you access to more / updated stuff. But by using those you relay on the integrity of others. If you're interested more, have a look at my sig.

---

