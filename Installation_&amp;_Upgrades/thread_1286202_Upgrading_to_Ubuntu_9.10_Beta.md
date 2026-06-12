---
title: "Upgrading to Ubuntu 9.10 Beta"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2009-10-08
Can I upgrade from Ubuntu 9.04 to 9.10 Beta, without having to go download and burning an ISO?
Thanks

---

### Post by mikewhatever on 2009-10-08
When Karmic is finished at the end of October, you'll see an Upgrade button in the Update Manager window. You can also upgrade now, but highly discouraged to do so for anything other then testing purposes.
[http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)
[http://ubuntuforums.org/showthread.php?t=1185036](http://ubuntuforums.org/showthread.php?t=1185036)

---

### Post by yo2boy on 2009-10-08
Do you mean not downloading ANYTHING at all?

If so, no. You can only Request/Buy an Ubuntu _9.04_ CD for now.

Alpha, Beta, RC releases are not on official CDs

---

### Post by gali98 on 2009-10-08
Just to clarify on the above users post, you will have to download all the new packages (which will be pretty big anyway.)
I think that is what they meant. :)
Kory

---

### Post by ineuw on 2009-10-08
My Ubuntu installation is a testing platform for learning, so I don't care if it crashes. Also, this is a dual boot setup, and when working in Windows, I backup using Acronis which recognizes the Linux partition. I upgraded to 9.04 by using the update manager, without having to download the ISO and burn it. I know that I need to download packages, (which is almost the same as downloading the ISO) but after reading the posts, I chickened out and decided to wait for the official release.

Thanks again to all, :-)

---

### Post by slakkie on 2009-10-09
Yes:

```

# GUI
sudo update-manager -d
# CLI
sudo do-release-upgrade -d

```

Backup your system before doing the upgrade, even when you don't mind a broken system. Restoring will help you to redo the upgrade process if needed.

Also, read the stickies in the Karmic forums, will safe you a lot of time and fixing issues :)

---

