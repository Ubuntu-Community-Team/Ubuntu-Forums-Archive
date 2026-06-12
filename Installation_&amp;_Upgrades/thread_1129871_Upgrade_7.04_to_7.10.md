---
title: "Upgrade 7.04 to 7.10"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by emmettpower on 2009-04-19
My wife has an old machine with 7.04 installed and I want to upgrade it to 7.10 and then onto 8.04. The problem I have is when I run the upgrade manager I get a message saying that fetching the necessary prerequisites has failed. I assume that this is because 7.04 is no longer supported. It is not finding the repositories when I try to update the software sources generating the following message:

"Could not download all repository indexes: The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]"

etc 

The network connection is fine. I have tried alternative download sites in the package manager. 

To try and get around the problem I have downloaded the 7.10 alternative CD. Am I safe to upgrade from that? And can I skip a step and upgrade from 7.04 to 8.04 using the 8.04 alternative CD? Or am I going to run the risk of hosing the system?

Thanks

---

### Post by Partyboi2 on 2009-04-19
You might be able to try [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/EOLUpgrades#7.04%20to%207.10") to upgrade to 7.10.
I am not sure how you would go upgrading using the alternate cd but you cannot skip releases when upgrading so you will need to go from 7.04-7.10-8.04-8.10

---

### Post by drs305 on 2009-04-19
The old repositories are maintained at:
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

These repositories can be used by people who don't want to upgrade to a newer version but may want to install packages from the old list.

It *may* be possible to use the repos listed there to upgrade from one old release to another. I would backup your data, perhaps make /home a separate partition so you can preserve your settings, and do a clean install.

For adding/changing repositories, review this ubuntu documentation page:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by zvacet on 2009-04-19
Maybe it is possible to do what you want but I can become complicated.Best thing you can do is fresh install.Be sure to have separate home and if you don´t have it make one following [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.After you make separate home do the fresh install on top of your existing Feisty root.

---

### Post by snowpine on 2009-04-19
Both 7.04 and 7.10 have reached their "end of life" and are no longer officially supported. I highly recommend backing everything up and doing a fresh install of 8.04 (or newer version). It will be "cleaner" and ultimately less frustrating in my opinion.

---

### Post by emmettpower on 2009-04-20
Looks like the weight of opinion is that I could create a mess so it would be wiser to do a fresh install.

Thanks for all the suggestions.

---

