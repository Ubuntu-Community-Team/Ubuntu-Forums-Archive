---
title: "feisty to gutsy"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by darwin_886 on 2008-12-31
I am trying to upgrade from feisty to gutsy (and eventually to ibex). I made sure feisty was fully up to date and also edited sources.list as instructed here:

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

However, update-manager fails with the following error messages:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]


Contents of sources.list file:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 


Any help would be appreciated. Thanks!

---

### Post by ForgeMaster on 2008-12-31
darwin,
  I am just below you on the list here.  We are trying to do similar things and I am getting the same error.  Maybe the server is down???
ForgeMaster

---

### Post by avtolle on 2008-12-31
I don't know if this will work, but what about trying to comment out all repositories except those added as instructed, then trying it again?

---

### Post by darwin_886 on 2008-12-31
Thanks - tried it. Update-manager just hangs.

---

### Post by bazillion on 2008-12-31
I'm having the same problem but I was also unable to edit the sources.list file.  When I right-click it comes up as a read-only file.

---

### Post by avtolle on 2008-12-31
OK, with your edited sources list as I suggested still in place, if you go to the terminal and do ```
sudo apt-get update && sudo apt-get upgrade
``` what occurs?

---

### Post by avtolle on 2008-12-31
> **bazillion said:**
> I'm having the same problem but I was also unable to edit the sources.list file.  When I click on it it comes up as a GUI, and the .save version is read-only.

How did you try to edit it? You should use a text editor, such as nano, or if you want a gui, gedit, to open the file to edit it, and you will need to be root to do so. E.G., in the terminal, ```
sudo nano /etc/apt/sources.list
```, make your changes and save it.

---

### Post by darwin_886 on 2008-12-31
Thanks - here's what I get:

kandp@kandp-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty Release.gpg [191B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/main Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/multiverse Translation-en_CA
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates Release.gpg [189B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/restricted Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/universe Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/multiverse Translation-en_CA
Get:3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security Release.gpg [189B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/multiverse Translation-en_CA
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) feisty-security/multiverse Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Then when I run update-manager, I get the same error message as before.

---

### Post by avtolle on 2008-12-31
Darwin, that's interesting. It shows your 7.04 is fully updated. For some reason, the update to your sources.list file isn't being recognized (as nearly as I can ascertain) by update-manager. It's been a while since 7.04 for me; what I'd try next is open Synaptic and try to reload your software sources (likely to be under third-party software) to see if that does the trick.

---

### Post by bazillion on 2008-12-31
Edited in nano, which worked - thanks!

Re-tried the update, which seemed to take longer but ultimtely hung with the following error msg:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]

Then ran sudo apt-get / upgrade and got (snip to end)

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource remporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I've got a lot of stuff going right now but nothing (to my admittedly very limited knowledge) as root or in that directory.  Suggest?

---

### Post by avtolle on 2008-12-31
bazillion, that error message occurs generally when there is a package manager open, such as Synpatic. Close down Synaptic (or update manager or whatever) and try it again.

---

### Post by bazillion on 2008-12-31
Thanks!  I did have a window open.

Tried it again and got:

...
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by oldos2er on 2008-12-31
> **bazillion said:**
> Thanks!  I did have a window open.

Tried it again and got:

...
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

 These files no longer exist on the server.

---

### Post by bazillion on 2008-12-31
> **oldos2er said:**
> These files no longer exist on the server.

Safe to continue update without them, or should I get an Ibex CD and start fresh?

---

### Post by oldos2er on 2008-12-31
> **bazillion said:**
> Safe to continue update without them, or should I get an Ibex CD and start fresh?

 That's a question only you can answer. If it was me, I would get either a Hardy or Ibex disk and start fresh.

---

### Post by jbdavid on 2009-01-01
After testing the 8.10 live CD on my system, I tried downloading the 7.10 Alternate install CD to do the upgrade from there.. 
 
But booting into it did not show me the upgrade menu I expected. 
-- turns out you have to Boot first, THEN install the CD, and then you'll get the upgrade menu.. 

-- By the way MOST of those missing packages are on the old-releases server, but the 7.04 installer STILL wants to find them on the us-archives server (well for me)  


I didn't upgrade EARLIER because I was worried that my hardware would not be supported..I guess that was a mistake.

---

