---
title: "uninstalling Ubuntu"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by limiz on 2009-03-06
OK I want to uninstall it and still keep my XP.. I find out that making xp 40% and unbuntu 60%... Used is up to 1.2Hz. when i switch back to XP. I know that i have 2.2Hz. But not it saying 1.0Hz. Making my XP run a little to slow for some of my games. But if i do uninstall. I'm going to re install unbuntu. But this time try to figure out how much less then xp and more to unbuntu.

1) Want to uninstall unbuntu. And still keep XP

2) I'm going to reinstall it but this time have low % to xp and more % to unbuntu. So this way when i go back to XP i have at less 1.80Hz. Witch should be just right to run the games i play on there.

[SIZE="3"]But don't know were to really start?[/SIZE]
I try posting in General Help... It A ghost town in there. @_@

---

### Post by martrn on 2009-03-06
You said that you want to uninstall Ubuntu keep your Xp and that Xp is taking up 40% and unbuntu is taking up 60%, I presume this is hard drive space, of how much I duon't know.

Usually processor speeds are measured in MHz GHz etc, and hard drive space is measured in MB, GB etc.  So I wouldn't know what 'Used is up to 1.2Hz' means.

You can repartition a hard drive using  gparted :
```

sudo apt-get install gparted
sudo gparted

```
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

GParted is the Gnome Partition Editor application to detect, resize and format hard disk drives and manipulate partition tables. You need to know how many MB/GB you have and wish to allocate to your new hard disk system first though before you use it.

As always using a partition manager application to detect and manipulate devices and partition tables can be a dangerous undertaking and can cause data loss on a large scale.

Installing Xp and Ubuntu side by side should not reduce your processor speed though.

---

