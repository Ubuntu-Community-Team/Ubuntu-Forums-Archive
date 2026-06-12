---
title: "Problem with update"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by mmeisam on 2009-02-05
Hello,

I am trying to upgrade my ubuntu installation from 7.04 to 8.10. I understand that i will have to perform a sequential upgrade and i have followed the instructions as outlined a [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) but for some reason it doesnt want to work for me i keep getting this error:

```
Failed to fetch http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/feisty-updates/universe/binary-i386/Packages.gz 404 Not Found [IP: 206.75.218.53 80]
```

I cant figure out why its trying to download from that mirror because i have commented out all sources except for the ones listed in on the upgrade page. This is what my sources.list looks like

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

#deb http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty main restricted multiverse
#deb-src http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty-updates main restricted multiverse
#deb-src http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty-updates universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

#deb http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty-security main restricted multiverse
#deb-src http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty-security universe main #Added by software-properties
#deb http://mirror.arcticnetwork.ca/pub/ubuntu/packages/ feisty-security universe


deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```

I have been searching the web for close to a week with no avail, hopefully someone can help me out here. Thanks for the help in advance.

Meisam

---

### Post by zvacet on 2009-02-07
After you changed your source list did you run

```
sudo apt-get update
```

to refresh your source list.

---

### Post by Kevbert on 2009-02-07
It looks like Ubuntu has be removed from that server. If you browse to [http://ubuntu.arcticnetwork.ca/ubuntu/dists/](http://ubuntu.arcticnetwork.ca/ubuntu/dists/) you'll find there's nothing there. You may be able to use the modified version of my Gutsy sources.list (attached, just renamed), as it looks like there are files on this server.

---

### Post by mmeisam on 2009-02-07
Thanks for the reply Kevbert, I have used the sources.list you provided and i get even more 404 errors

```
http://mirror.arcticnetwork.ca/pub/ubuntu/packages/dists/feisty-updates/universe/binary-i386/Packages.gz: 404 Not Found [IP: 206.75.218.53 80]
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 404 Not Found
http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz: 404 Not Found

```

Baisically [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/) does not exist and [http://mirror.arcticnetwork.ca/](http://mirror.arcticnetwork.ca/) is still being used.

Meisam

---

### Post by avtolle on 2009-02-07
Take a look at this thread, and see if it helps you: [http://ubuntuforums.org/showthread.php?t=1063043](http://ubuntuforums.org/showthread.php?t=1063043)

---

### Post by mmeisam on 2009-02-07
I tried that and the error i was getting is in my first post. Articnetworks.ca is not mentioned anywhere in my sources.list file yet its still trying to download from it.

Meisam

---

### Post by Kevbert on 2009-02-08
Make sure that it doesn't occur under Software Sources (Third party software tab). If it does then untick it. The source may still be found under /etc/apt/sources.list.d/
It may also be worth trying a server nearer to you in Canada.  If that doesn't work, maybe it means a clean install as distribution updates can be a little problematic. Don't forget to backup all your data. You can back up a list of all installed packages with
```
sudo dpkg --get-selections > packback.txt
```
Copy the packback.txt file to your new installation and then to reinstall
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < packback.txt
sudo aptitude install dselect-upgrade
```

Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6319924&postcount=4") as it offers you a better solution.

---

