---
title: "upgrading from hardy to newer release???"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Lee83 on 2009-04-26
after using Hardy for what seems an eternity ive recently decided to upgrade to a newer release,however...ive spent a great deal of time "perfecting" (lol hardly) my desktop and applications to suit my needs and dont want to lose everything ive worked hard for,is there a way to upgrade but keep all my old settings etc,i understand that there might be some compatability issues because hardy is a long well serviced distro and some apps might not run well or at all in jaunty for instance,a new upgrade withouit a clean install is what im after and if its possible how do i go about it..

---

### Post by Partyboi2 on 2009-04-26
Hi, you can do the recommend network upgrade 
[https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)
You  cannot miss out releases when doing a upgrade so you will need to upgrade first to Intrepid before going to Jaunty.

---

### Post by Tim Sharitt on 2009-04-26
If you want to do a clean install, you could back up your home directory and restore it after the install or move your home directory to a separate partition. How to create a separate home partition- [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That being said, I don't know that you would have much of a problem upgrading, unless you are using applications that are no longer supported after 8.04.

---

### Post by Triptol on 2009-04-26
If you are going for a new installation there are some things to consider:

[LIST]
[*]Your settings are in your homedirectory (in all those hidden directories and files). Make sure you do not lose them. If I do a new install, I only format my root partition and don't touch my homepartition. Normally the system comes back almost the way I left it.
[*]If you do a new install, all programs installed by you from the repository will not be there, so you need to reinstall them. Check here for more info on how to do that: [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html")
[*]All your custom programs (applications not installed from the repositories or installed through custom repositories) will not be available after a new install. This will be the minority, but you should check these before going the "new install" way.[/LIST]

---

### Post by Lee83 on 2009-04-26
ive tried the new release in virtualbox and have it on there,first impressions is its not really any different from ibex or hardy for that matter,sayin that i havent really delved into it that far,jury is still out on the full upgrade,thanks for all your info people.

---

