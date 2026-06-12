---
title: "Update manager broken after upgrade to Jaunty"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2009-04-25
Please help.

I have been upgrading my system since Feisty and I am very happy with it.

However, the latest Jaunty upgrade seems to have broken the upgrade system in my computer.

(I upgraded from an iso-image of the Jaunty-alternative CD. That went OK, but I must update packages now.)

When I now activate the update manager (Gnome) the following happens:

update mgr
"not all updates can be installed, run a partial upgrade"
<enter my pwd>
"running partial upgrade", "preparing to upgrade", "start upgrade?"
"2 packages will be removed, 33 p. installed and 18 p. upgraded"
I click "start upgrade" but the program just dies and does nothing.

If I repeat the procedure the same thing happens.

It seems the update manager is "broken"?

Thanks for advice how to get my update manager back on track :)


EDIT: It seems that I can read the list of packages (in update manager) and MANUALLY manipulate each package in Synaptic. But this seems like a long way to go and I still don't know it the update manager will work with future updates.

---

### Post by Merovius on 2009-04-25
Same here. I also upgraded via an alternate CD.

---

### Post by Northsider on 2009-04-26
Same here.  I included screenshots in my posts here:

[http://ubuntuforums.org/showthread.php?t=1138396](http://ubuntuforums.org/showthread.php?t=1138396)

---

### Post by yc2 on 2009-04-26
Thanks, I saw the advice about using aptitude
```
sudo aptitude dist-upgrade
```
I just worked through all the packages manually using Synaptic. If the update managaer doesn't work for the next update, I may try that advice.

---

### Post by yc2 on 2009-04-28
I read the list of packages in the update manager and installed/updated/removed through Synaptic.
Ater that my system has functioned well for 24 hrs and now I got the first new update that could be performed in the ordinary way (update manager).

Since I usually use apt-get or Synaptic for installation, maybe it was good for me to use Synaptic for the manual reinstallation. (There is something about the dependencies ...)

So my system seems to be back to normal now.

---

