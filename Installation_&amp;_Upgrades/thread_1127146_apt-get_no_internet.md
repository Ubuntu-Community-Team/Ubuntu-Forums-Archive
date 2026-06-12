---
title: "apt-get no internet"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by uWitchDoctor on 2009-04-16
I am going to follow [color=red][THIS](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))[/color] in order to get my new Belkin F5D7050 V3 working on ubuntu. I deliberately choose this card as I understand the ralink chip set is one of the better supported chipsets in linux. This is not my problem as of current. My issue is regarding some of the commands within the guide namely the ones that ask me to perform actiobs such as *"Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)"*

My question is, if you are trying to use commands that require access to the internet from a PC that does not have the internet how do you do this?

I am hoping to be able to use another PC in order to download all the files and dependencies I need and then to manually install them on my ubuntu machine.

Cheers

---

### Post by Partyboi2 on 2009-04-16
Hi, one option is to manually download the packages required from a machine connected to the Internet and transfer them over to the machine without Internet and install by double clicking on the deb packages. You can download the packages from  [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/"), this process could take awhile if there are lots  of dependencies. 
Another option (probably better) is to use [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/") to install the packages required.

---

