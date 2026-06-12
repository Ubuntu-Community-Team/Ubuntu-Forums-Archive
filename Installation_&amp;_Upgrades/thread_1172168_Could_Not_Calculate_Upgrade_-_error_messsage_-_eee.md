---
title: "Could Not Calculate Upgrade - error messsage - eeebuntu"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by simgriff on 2009-05-28
When I run Update Manager I am getting "Not all updates can be installed" and "Could not calculate upgrade" error messages.

Another thread someone suggested doing sudo apt-get but I don't know what the results mean:

Fetched 310B in 32s (10B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems

The results of sudo apt-get upgrade is:

The following packages have been kept back:
openoffice.org openoffice.org-base openoffice.org-base-core
openoffice.org-calc openoffice.org-common openoffice.org-core
openoffice.org-draw openoffice.org-filter-binfilter openoffice.org-gnome
openoffice.org-gtk openoffice.org-impress openoffice.org-math
openoffice.org-officebean openoffice.org-report-builder-bin
openoffice.org-style-andromeda openoffice.org-style-crystal
openoffice.org-style-human openoffice.org-style-tango openoffice.org-writer
python-uno uno-libs3 ure
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.

I don't understand any of this - is someone able to help a Linux Newbie???
I need to know what it means and then what to do about it.

Thanks

---

### Post by jacksaff on 2009-05-28
apt-get upgrade will upgrade all installed packages but it will not install any new packages. The likely problem you have is that one of the upgradable packages needs a new package to be installed.

If the new packages are somewhat experimental or very, very recent to the repository then that other package might not be available.

apt-get dist-upgrade does an upgrade + installs any new packages. It didn't use to be recommended to dist-upgrade ubuntu. Not sure why. 

"aptitude safe-upgrade" should upgrade your system without any hassle.

The gpg messages are because you have added a repository but not added it's gpg key which allows the packages to be signed so you know who they are coming from. Do a search for 60D11217247D1CFF and you should find out how to install the key. It doesn't hurt not to, AS LONG AS you are absolutely sure of the source of the packages.

---

