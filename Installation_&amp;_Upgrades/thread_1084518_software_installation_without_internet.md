---
title: "software installation without internet"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by kask1984 on 2009-03-02
hi every body. i want to install softwares on a system which is not connected to internet. my friend system has net connection and he installed all required softwares by downloading from net.

i followed this  method.
i gave command in my friend system
&#8220; sudo cp -R /var/cache/apt/archives /media/SHIVA&#8221;

In my system i gave these commands

&#8220; cd /media/SHIVA/archives &#8221;

&#8220; sudo cp -R * /var/cache/apt/archives &#8221;

&#8220; sudo dpkg -i * &#8221;

after some time i got upgraded (installed updates) but it is failed to install softwares like vlc,mplayer etc.
it is displaying message that u have broken packages.


my aim is to install softwares offline(without internet) .

please help me 
i am and my friend using ubuntu 8.10 .

many many thanks in advance

---

### Post by Partyboi2 on 2009-03-02
You could use a program called [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/") for installing software without a Internet connection.

---

