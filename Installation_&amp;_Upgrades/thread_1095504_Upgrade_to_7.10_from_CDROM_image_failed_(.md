---
title: "Upgrade to 7.10 from CDROM image failed :("
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2009-03-13
Hello all,
 i am trying desperately to upgrade my 7.04..
I have downloaded a 7.10 image on a CD and tried  upgrade from CD, but installation process failed with message 'could not calculate the upgrade'

hERE'S what in my main.log  


2009-03-13 23:20:35,014 INFO release-upgrader version '0.81' started
2009-03-13 23:20:42,521 DEBUG lsb-release: 'feisty'
2009-03-13 23:20:42,522 DEBUG _pythonSymlinkCheck run
2009-03-13 23:20:43,665 DEBUG checkViewDepends()
2009-03-13 23:20:43,665 DEBUG doUpdate() will not use the network because self.useNetwork==false
2009-03-13 23:20:48,018 DEBUG Foreign: 
2009-03-13 23:20:48,018 DEBUG Obsolete: libdivxencore0-binary ndiswrapper-utils realplay linux-image-2.6.15-29-386 libdivx0-binary linux-image-2.6.15-27-386 skype linux-image-2.6.15-26-386 linux-image-2.6.15-28-386 linux-restricted-modules-2.6.15-29-386 libpq4 linux-restricted-modules-2.6.15-28-386 gtk-sopcast libdivxdecore0-binary linux-restricted-modules-2.6.15-27-386 linux-image-2.6.17-12-386 libgail17 gbtsco picasa linux-restricted-modules-2.6.15-26-386 automatix2 frostwire bmp-docklet linux-restricted-modules-2.6.17-12-386
2009-03-13 23:20:48,044 DEBUG updateSourcesList()
2009-03-13 23:20:48,207 DEBUG rewriteSourcesList()
2009-03-13 23:20:48,208 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted'
2009-03-13 23:20:48,209 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted' updated to new dist
2009-03-13 23:20:48,209 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe'
2009-03-13 23:20:48,209 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe' updated to new dist
2009-03-13 23:20:48,209 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse'
2009-03-13 23:20:48,210 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse' updated to new dist
2009-03-13 23:20:48,210 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe'
2009-03-13 23:20:48,210 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe' updated to new dist
2009-03-13 23:20:48,210 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe'
2009-03-13 23:20:48,211 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe' updated to new dist
2009-03-13 23:20:48,211 DEBUG examining: 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse'
2009-03-13 23:20:48,214 DEBUG entry '# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse' was disabled (unknown mirror)
2009-03-13 23:20:48,215 DEBUG examining: 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse'
2009-03-13 23:20:48,218 DEBUG entry '# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse' was disabled (unknown mirror)
2009-03-13 23:20:48,218 DEBUG examining: 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse'
2009-03-13 23:20:48,222 DEBUG entry '# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse' was disabled (unknown mirror)
2009-03-13 23:20:48,222 DEBUG examining: 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse'
2009-03-13 23:20:48,225 DEBUG entry '# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse' was disabled (unknown mirror)
2009-03-13 23:20:48,226 DEBUG examining: 'deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse'
2009-03-13 23:20:48,229 DEBUG entry '# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse' was disabled (unknown mirror)
2009-03-13 23:20:48,229 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-backports main/debian-installer'
2009-03-13 23:20:48,229 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-backports main/debian-installer' updated to new dist
2009-03-13 23:20:55,124 DEBUG AptCdrom.add() called with '/cdrom'
2009-03-13 23:21:25,032 DEBUG AptCdrom.add() returned: 1
2009-03-13 23:21:25,032 DEBUG doUpdate() will not use the network because self.useNetwork==false
2009-03-13 23:21:25,704 DEBUG demoted: 'binfmt-support evms evms-ncurses feisty-session-splashes festlex-cmu festlex-poslex festvox-kallpc16k gcj-4.1-base gij-4.1 gnome-cups-manager libdb3 libevms-2.5 libgcj7-jar libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgtk1.2 libgtk1.2-common liblzo1 libportaudio0 libslab0 libstlport5.1 libxml1 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl openoffice.org-filter-mobiledev pmount rcs ttf-baekmuk vnc-common xmms xvncviewer'
2009-03-13 23:22:13,654 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2009-03-13 23:22:13,654 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2009-03-13 23:22:13,918 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2009-03-13 23:22:13,918 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2009-03-13 23:22:13,918 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2009-03-13 23:22:13,953 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2009-03-13 23:22:13,981 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2009-03-13 23:22:13,981 DEBUG running gutsyQuirks handler
2009-03-13 23:22:13,981 DEBUG Kernel uname: '2.6.20-17-386' 
2009-03-13 23:22:14,006 DEBUG UP kernel on SMP system!?!
2009-03-13 23:22:14,007 DEBUG Selecting new kernel 'linux-image-generic'
2009-03-13 23:22:14,135 DEBUG Marking 'ubuntu-desktop' for upgrade
2009-03-13 23:22:14,439 DEBUG Can't mark 'ubuntu-desktop' for upgrade (E:Unable to correct problems, you have held broken packages.)



could anyone help m eout?

thanks in advance and regards
 marco

---

### Post by upchucky on 2009-03-13
I have to assume that you have a back up of your files, if true then why not just install 7.10 and restore the files to it? seems to me to be the way to go when a upgrade fails.

on the other hand, have you tried to change sources, i had a upgrade that wanted files from several sources, i had to switch the sources for it to complete. it may be looking for sources that are dependent on the net, but it is looking at the cdrom for them instead? or vice-versa.

---

### Post by BertP on 2009-04-25
I am having a similar problem,  I have 7.10 and want to upgrade to 8.04
(hardware issues prevented me from upgrading before now)

anyway I downloaded the "alternate installer" ISO  which I think can be used as a cd version of the online update...  anyway the install fails and at the very end of the main.log  I also have "*Unable to correct problems, you have held broken packages.)"  Is this because the Gutsy infrastructure has already been taken down and no longer available for download?

---

