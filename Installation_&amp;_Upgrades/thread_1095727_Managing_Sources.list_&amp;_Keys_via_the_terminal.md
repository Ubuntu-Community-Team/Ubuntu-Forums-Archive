---
title: "Managing Sources.list &amp; Keys via the terminal"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by mirrorhall on 2009-03-14
[COLOR="Navy"]:idea: Keep your [COLOR="Magenta"]sources.list[/COLOR] organised, record keys when adding new repositories and back it up to a safe place[/COLOR]

*Intrepid Example via Japanese/Hong Kong Mirrors*

```
[COLOR="DarkRed"]sudo gedit /etc/apt/sources.list[/COLOR]
```
> ## --------------------
## intrepid repositories
## --------------------

deb [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid main restricted universe multiverse
deb [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-proposed main restricted universe multiverse
deb [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


## ---------------
## intrepid sources
## ---------------

deb-src [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-updates main restricted universe multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-security main restricted universe multiverse
deb-src [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-proposed main restricted universe multiverse
deb-src [http://ftp.ecc.u-tokyo.ac.jp/ubuntu/](http://ftp.ecc.u-tokyo.ac.jp/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

## ------------------
## other resources
## ------------------

## Medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free 

## Launchpad
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main

## Medibuntu Sources
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free 

## Launchpad Sources
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main

################
### Imported Keys ###
################

# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 60D11217247D1CFF
# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9ABD04E22847688F
# [COLOR="SeaGreen"]apt-key adv --recv-keys --keyserver keyserver.ubuntu.com[/COLOR] [COLOR="RoyalBlue"]632D16BB0C713DA6[/COLOR]

[COLOR="Navy"]**     Keep a record of the key requested by aptitude/apt-get after you add a new repository** [/COLOR] 
 
```
[COLOR="DarkRed"]sudo aptitude update[/COLOR]
```
> Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [COLOR="RoyalBlue"]632D16BB0C713DA6[/COLOR]
W: You may want to run apt-get update to correct these problems
```
[COLOR="DarkRed"][COLOR="SeaGreen"]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com[/COLOR] [COLOR="RoyalBlue"]632D16BB0C713DA6[/COLOR][/COLOR]
```
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
gpg: requesting key 0C713DA6 from hkp server keyserver.ubuntu.com
gpg: key 0C713DA6: public key "Launchpad PPA for Fabien Tassin" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

**     All done!**

---

### Post by Elep.Repu on 2009-08-09
Very organized. Impressive.
Thanks a bunch for your tutorial.

---

