---
title: "Failed to install kubuntu-desktop in ubuntu 8.10"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Maxei on 2009-05-31
Hi, I want to install KDE 4.2 in Ubuntu 8.10. The errors I got are the following. Any ideas to solve it? Thanks

~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: dragonplayer but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
                   Depends: kde-zeroconf but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kuser but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: adept but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: gdebi-kde but it is not going to be installed
                   Recommends: guidance-power-manager but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kde-printer-applet but it is not going to be installed
                   Recommends: kdebase-plasma but it is not going to be installed
                   Recommends: kdebluetooth but it is not going to be installed
                   Recommends: kdegraphics-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-kresources but it is not going to be installed
                   Recommends: kdepim-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdeplasma-addons but it is not going to be installed
                   Recommends: kdesudo but it is not going to be installed
                   Recommends: kgrubeditor but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: konqueror-plugin-searchbar but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kopete but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: krdc but it is not going to be installed
                   Recommends: krfb but it is not going to be installed
                   Recommends: ktimetracker but it is not going to be installed
                   Recommends: ktorrent but it is not going to be installed
                   Recommends: kubuntu-docs but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: kvkbd but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: okular-extra-backends but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: plasmoid-quickaccess but it is not going to be installed
                   Recommends: update-notifier-kde but it is not going to be installed
E: Broken packages

---

### Post by oldos2er on 2009-05-31
Try running **sudo apt-get install -f** to fix your broken packages.

 Do you have all repositories enabled?

---

