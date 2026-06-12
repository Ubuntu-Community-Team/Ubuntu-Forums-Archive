---
title: "[SOLVED] 8.10 and new Software updates"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by gdonwallace on 2008-12-09
I came in this morning and found that some updates where ready for 8.10.

I start the update manager and it tells me that it can only do a partial update because of a possible problem.  It lists a few things that may be the problem:
     Last update did not complete
     problem with installed software
     ect....

I choose partial update, it starts by checking the system and installed software and then pops a window with a list of programs that I am told the update will not run because of.  The only software that is on the list is OpenOffice 3.0

I would like to do the update, but I don't have time to uninstall / reinstall OpenOffice. If that is the only way, then I'll report that as a bug and see if they can fix it.

---

### Post by taurus on 2008-12-09
Close down the update-manager.  Then, open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by gdonwallace on 2008-12-09
When I run sudo **apt-get update** I get the following

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 1B in 4s (0B/s)  
Reading package lists... Done

When I run sudo **apt-get upgrade** I get the following:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-writer python-uno
The following packages will be upgraded:
  compiz-fusion-plugins-main libdeskbar-tracker libtracker-gtk0
  libtrackerclient0 libv4l-0 openoffice.org-common openoffice.org-emailmerge
  openoffice.org-filter-mobiledev openoffice.org-java-common
  openoffice.org-style-human tracker tracker-search-tool ttf-opensymbol
  uno-libs3 ure
15 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 29.6MB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y

WARNING: The following packages cannot be authenticated!
  openoffice.org-style-human openoffice.org-common openoffice.org-emailmerge
  openoffice.org-java-common openoffice.org-filter-mobiledev ttf-opensymbol
  ure uno-libs3
Install these packages without verification [y/N]?

---

### Post by taurus on 2008-12-09
You get that warning message probably due to [http://ppa.launchpad.net](http://ppa.launchpad.net) in your /etc/apt/sources.list.

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by gdonwallace on 2008-12-09
This is my **/etc/apt/sources.list**

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu    
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's          
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main <--- This may be the issue then.  When I updated to 8.04, OpenOffice 3.0 was not part of the repository.  Not sure if it is yet or not, have not checked to see.

---

### Post by taurus on 2008-12-09
OpenOffice is still version 2.4.1 on my Intrepid.  So if you want to upgrade it to 3.0 from that repo, then you have to answer the question with y.

---

### Post by gdonwallace on 2008-12-09
I went ahead an answered Yes to the question and the update went through

Thanks for the help.

---

### Post by gdonwallace on 2008-12-12
I edited the line in /etc/apt/sources.list so that it would not process when running the update:

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main <---

This seems to have fixed the problem.  Once OpenOffice 3.0 becomes part of the distro or shows up in the repository, I'll change it back and should not have any problems.

---

