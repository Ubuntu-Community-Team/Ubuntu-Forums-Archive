---
title: "How do I remove all games?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by andrewkk on 2009-11-11
How can I uninstall all of the games that are included with Ubuntu 9.10 by default?

In previous versions of Ubuntu, removing one game caused all the rest to be removed due to some kind of dependency. Now, in Karmic, this does not happen. I do not know the individual package names of each game. Removing the package gnome-games did not cause any games to be removed.

---

### Post by gasull2 on 2009-11-12
Same problem over here.

---

### Post by running_rabbit07 on 2009-11-12
Go to System>Administration>Synaptic Package Manager and search for "gnome games." It may or may not have a dash in it. Highlight it to click remove.

---

### Post by andrewkk on 2009-11-12
> **running_rabbit07 said:**
> Go to System>Administration>Synaptic Package Manager and search for "gnome games." It may or may not have a dash in it. Highlight it to click remove.

Thank you for the suggestion. Removing this package, however, did not remove any games. It appears to have no effect at all. Does it make a difference that I used apt-get[SIZE="1"]*[/SIZE] rather than Synaptic? Removing this package was the first thing I tried and I don't usually use Synaptic.

[SIZE="1"]* technically, [wajig]("http://www.togaware.com/linux/survivor/Wajig_Overview.html"), but I think it calls apt-get[/SIZE]

---

### Post by audiomick on 2009-11-12
Try this. I don't know if there's a more elegant way, but this should work.
Some of the names here might be wrong; my computer talks German, and I am translating on a "best bet" basis ;)
Open the software manager at the bottom of the applications menu.
Go to the drop down that tells it what to show you and select "installed applications"
Go to the side and tell it to show you the games.
you should now be only seeing the installed games.
deselect them all and tell it to apply changes

Michael

---

### Post by andrewkk on 2009-11-12
> **audiomick said:**
> Open the software manager at the bottom of the applications menu.
Go to the drop down that tells it what to show you and select "installed applications"
Go to the side and tell it to show you the games.
you should now be only seeing the installed games.
deselect them all and tell it to apply changes

Thank you, but in Ubuntu 9.10 this interface has been replaced. Two behaviors of the [new interface]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center") make this approach impossible:
[LIST=1]
[*]There is no way to filter for installed games. While the "Get Free Software" section does allow you to narrow down the list to only items in the "Games" category, the "Installed Software" section does not allow for this kind of filtering.
[*]Packages must be removed one at a time. Unlike Synaptic and the previous Add/Remove interface, there is no queue of packages to be installed; changes are applied immediately after marking each package. This behavior makes the removal of multiple packages via this interface is a very tedious process.
[/LIST]

---

### Post by running_rabbit07 on 2009-11-12
> **andrewkk said:**
> Thank you for the suggestion. Removing this package, however, did not remove any games. It appears to have no effect at all. Does it make a difference that I used apt-get[SIZE=1]*[/SIZE] rather than Synaptic? Removing this package was the first thing I tried and I don't usually use Synaptic.

[SIZE=1]* technically, [wajig]("http://www.togaware.com/linux/survivor/Wajig_Overview.html"), but I think it calls apt-get[/SIZE]

That is odd. I don't know the commands to uninstall. Are you using Kubuntu or Ubuntu?

---

### Post by gasull on 2009-11-13
```
sudo aptitude remove gnome-games-common
```

---

### Post by andrewkk on 2009-11-13
> **gasull said:**
> ```
sudo aptitude remove gnome-games-common
```

Awesome, this did it. Thanks!

---

### Post by Big Iain on 2009-11-13
> **andrewkk said:**
> Awesome, this did it. Thanks!

what a killjoy you must be

---

### Post by audiomick on 2009-11-13
> **Big Iain said:**
> what a killjoy you must be

I think he's a teacher...;)

---

### Post by mattlindsay on 2009-11-22
Perfect, sorted my issue right out. Thanks!

Matt

---

