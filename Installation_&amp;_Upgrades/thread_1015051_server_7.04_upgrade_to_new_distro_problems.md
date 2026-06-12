---
title: "server 7.04 upgrade to new distro problems"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by caveman-jim on 2008-12-18
I'm trying to update an Ubuntu server running 7.04 to 8.04, and can't as it appears that the US archives web repository is missing a folder - /fiesty.

Looking at the [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) directory there is a dapper, intrepid etc. path but no fiesty. Is this by design or an accident?

My update process is:

sudo apt-get updates
sudo apt-get upgrade
sudo do-release-upgrade

At the final step I get errors reported as that packages can't be found:

[IMG]http://img517.imageshack.us/img517/9482/ubuntumissingrepositoribj0.png[/IMG]

I'm not very experienced with linux/ubuntu, so please don't hestiate to let me know if I'm doing something stupid, need to read the manual, or am going about someing bassackwards :p

Is there a way to point it at another set of repositories? Edit sources.list, to point to what?

---

### Post by overdrank on 2008-12-18
Hi and Feisty has reached its end of life so no support. You can try and use the alternate cd to upgrade to a newer version or modify your source list to the newer repos. I do not advise this as it is likely to cause issues.

---

### Post by caveman-jim on 2008-12-18
Thanks for the quick response! So the way forward from here is rebuild, new install of 8.04LTS and go from there?

---

### Post by kostkon on 2008-12-18
You can't upgrade from 7.04 to 8.40 directly but first to 7.10 and then 8.04.

If you still want to do it, then follow [this guide]("https://help.ubuntu.com/community/GutsyUpgrades") to upgrade to 7.10 (pay attention to [this part]("https://help.ubuntu.com/community/GutsyUpgrades#Fully%20updating%207.04")) and then [this guide]("https://help.ubuntu.com/community/HardyUpgrades") to upgrade to 8.04.

---

### Post by caveman-jim on 2008-12-18
Great! thanks for the help, I appreciate it.

---

### Post by caveman-jim on 2008-12-19
OK, so I added the old-releases lines to my sources.list, did and apt-get update and apt-get upgrade which appeared to work, but when attempting the do-release-upgrade I get an error referring to the missing packages on the archive repositories, still.

Am I missing something obvious? Should I be commenting out lines in sources.list to compensate for the new archives on old-release mirror?

---

### Post by kostkon on 2008-12-19
> **caveman-jim said:**
> OK, so I added the old-releases lines to my sources.list, did and apt-get update and apt-get upgrade which appeared to work, but when attempting the do-release-upgrade I get an error referring to the missing packages on the archive repositories, still.

Am I missing something obvious? Should I be commenting out lines in sources.list to compensate for the new archives on old-release mirror?
Yes, you need to comment out the old/previously existing lines, of course!

---

### Post by caveman-jim on 2008-12-19
d'oh! Ok, edited sources.list and commented all the existing deb entries (not deb-src; is that wrong?), added in the three new lines, and still getting a network error:

[IMG]http://img152.imageshack.us/img152/3484/ubuntufailix6.png[/IMG]

Retried with all standard entries commented, and get an error message regarding no mirror; answer yes to continue, can't find a bunch of packages and fail.

[IMG]http://img340.imageshack.us/img340/663/ubuntunomirroraz6.png[/IMG]

so is it time to download the 7.10 alt CD and upgrade via that, or is there something else I'm overlooking? do I need to add back some sources entries?

---

### Post by kostkon on 2008-12-19
> **caveman-jim said:**
> d'oh! Ok, edited sources.list and commented all the existing deb entries (not deb-src; is that wrong?)
You have to comment out everything, even the *deb-src* lines.
> **caveman-jim said:**
> Retried with all standard entries commented, and get an error message regarding no mirror; answer yes to continue, can't find a bunch of packages and fail.
Hmmmm, strange. After fixing the *sources.list*, have you tried a
```
sudo apt-get update && sudo apt-get upgrade
```
to be sure that you are up-to-date. It is important that you are.
Then try again to dist-upgrade.

If the no valid mirror error message appears again after doing the above, just ignore it again and select yes.

---

### Post by caveman-jim on 2008-12-19
> **kostkon said:**
> Then try again to dist-upgrade.


Stupid question - what's the difference between apt-get dist-upgrade and do-release-upgrade? I've been using the latter thus far, is it the term dist-upgrade interchangable with using the update-manager to update, or is it a different process?

---

### Post by caveman-jim on 2008-12-19
OK, i edited the sources and removed all existing entries, added in the three entries to point to old-releases. did an update and upgrade, that went fine. install-manager-core was installed as part of the updates, so I tried a do-release-upgrade and it failed again as screenshot above indicated - asked to overwrite sources to find mirror, then quit. my edited sources was unchanged.

---

