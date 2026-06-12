---
title: "Installing NVIDIA 190 drivers erases lots of packages"
date: 2009-09-14
forum: Hardware
---

### Post by WindPower on 2009-09-14
Numerous guides say to add [this PPA](https://launchpad.net/~nvidia-vdpau/+archive/pp) to install the newest NVIDIA 190 drivers. However, after adding the repository successfully, here's what happens:
```
$ sudo apt-get install nvidia-glx-190 nvidia-190-modaliases
Reading package lists... Done                                                                  
Building dependency tree                                                                       
Reading state information... Done                                                              
Some packages could not be installed. This may mean that you have                              
requested an impossible situation or if you are using the unstable                             
distribution that some required packages have not yet been created                             
or been moved out of Incoming.                                                                 
The following information may help resolve the situation:                                      

The following packages have unmet dependencies:
  nvidia-glx-190: Depends: nvidia-190-libvdpau (>= 190.32) but it is not going to be installed
E: Broken packages
```
Alright, so it seems I have to install nvidia-190-libvdpau... However, when I do, I see this:
```
$ sudo apt-get install nvidia-glx-190 nvidia-190-modaliases nvidia-190-libvdpau
Reading package lists... Done                                                                                      
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxrandr-dev libexpat1-dev pkg-config libxklavier15 pkg-kde-tools libpolkit-qt0 comerr-dev libxfixes-dev libgl1-mesa-dev
  x11proto-xinerama-dev xlibmesa-gl-dev x11proto-render-dev libxi-dev libsqlite0 libtag-extras0 libkrb5-dev mysql-server-core-5.0
  libfontconfig1-dev liblcms1-dev x11proto-randr-dev libxinerama-dev libglu1-xorg-dev mesa-common-dev akonadi-server x11proto-fixes-dev
  libglu1-mesa-dev x11proto-xext-dev libssl-dev qt4-qmake libxmu-dev libxext-dev amarok-common libglib2.0-dev libfreetype6-dev
  libsoprano-dev libaudio-dev libpq-dev libkadm55 kdebase-workspace-wallpapers libphonon-dev kdepim-runtime-data libxmu-headers
  libxrender-dev libxft-dev kdewallpapers libqt4-scripttools compizconfig-backend-kconfig marble-data libmng-dev libsqlite0-dev
  libjpeg62-dev libkdcraw7 libxcursor-dev libpng12-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-190-kernel-source
The following packages will be REMOVED:
  akregator amarok apport-qt ark automoc compiz-kde dolphin dragonplayer fusion-icon gdebi-kde gwenview install-package jockey-kde
  kaddressbook kamera kate kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-plasma kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-workspace-bin kdebase-workspace-dev kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5
  kdebluetooth kdegraphics-strigi-plugins kdelibs5-dev kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources
  kdepim-runtime kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdeplasma-addons kdesudo kdm kfind khelpcenter4 klipper kmag
  kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc
  krfb kscreensaver kscreensaver-xsavers kscreensaver-xsavers-extra kscreensaver-xsavers-webcollage ksnapshot ksysguard ksystemlog
  ktimetracker kubuntu-desktop kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libkabcommon4 libkcddb4
  libkdecorations4 libkdepim4 libkleo4 libkonq5 libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkpgp4 libksieve4 libkwineffects1
  liblancelot0 libmarble4 libmimelib4 libokularcore1 libplasma3 libqedje0 libqt4-dev libqt4-opengl-dev libqt4-webkit libqtscriptbindings1
  libqzion0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x nvidia-185-kernel-source
  nvidia-185-libvdpau nvidia-glx-185 okular okular-extra-backends phonon phonon-backend-xine plasma-dataengines-addons
  plasma-dataengines-workspace plasma-runners-addons plasma-wallpapers-addons plasma-widget-folderview plasma-widget-lancelot
  plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit-kde printer-applet python-kde4 python-plasma
  python-qt4 quassel software-properties-kde system-config-printer-kde systemsettings update-manager-kde update-notifier-kde xorg yakuake
The following NEW packages will be installed:
  nvidia-190-kernel-source nvidia-190-libvdpau nvidia-190-modaliases nvidia-glx-190
0 upgraded, 4 newly installed, 132 to remove and 0 not upgraded.
Need to get 21.7MB of archives.
After this operation, 317MB disk space will be freed.
Do you want to continue [Y/n]?
```
And I'm **really** hesitant to do this, because I can see plenty of seemingly unrelated packages that are going to be removed (amarok? Why remove amarok for a new graphics driver?) and packages I'd rather not remove (kdebase-*, systemsettings. and even xorg!).

So what should I do? I'm currently using the 185 drivers on NVIDIA GeForce 9600M GT on a MacBook Pro (model 5,3), running Kubuntu 9.04 64-bit.

---

### Post by coffeefan on 2009-10-13
I have same problem with Karmic 9.10. After installing kubuntu-restricted-extras (package version 36) I'm unable to install nvidia-glx-190 driver again (NVidia driver was changed from 190 to 185). I need NVidia 190 beta driver to get picture on my screen, 185 won't work. Tried to apt-get remove kubuntu-restricted-extras, but it won't change anything.

I'm typing this from my Vista laptop as my Kubuntu box is now in unusable state, either I remove X+KDE-packages or have recovery mode text console... I do not want to reinstall system again if it is avoidable.

---

### Post by dabl on 2009-10-13
If the VDPAU is not a huge deal and you just need an Nvidia driver installed, this should work:

[http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892](http://kubuntuforums.net/forums/index.php?topic=3100807.msg164892#msg164892)

Note, for 9.10 and subsequent, the command to stop KDM is ```
sudo service kdm stop
``` versus the prior ```
sudo /etc/init.d/kdm stop
```

I'm running the 190.36 Beta driver on 9.10 with no obvious problems.

---

### Post by WindPower on 2009-10-13
I solved this using [this PPA](https://launchpad.net/~thefirstm/+archive/ppa) instead.

---

### Post by coffeefan on 2009-10-13
Thanks for replies. Installing NVidia 190 beta manually indeed did the trick.

However, I tried to avoid installing driver manually as it will break at every kernel/X update. I'm so fed up with that manually installed driver... I've been Fedora+NVidia user for several years. :)

Also it seems that Karmic nvidia-glx-185 package is broken, installed it on clean, new 9.10 installation using Activate on Hardware Drivers. I've used NVidia driver 185.18.36 on Fedora without problems.

@Windpower: thanks, I will try driver from that repository.

---

### Post by psychok9 on 2009-10-27
I've the same problem with Karmic+190.xx PPA drivers, and I don't want using manual drivers that going fast corrupted after a updated kernel.

---

### Post by mce230 on 2009-11-13
Using the PPA recommended by WindPower ([https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)) solved the dependency problems that I was running into.  For me, it was that libxine1-bin depended specifically on nvidia-185-libvdpau instead of the nvidia-190-libvdpau that I had installed, and then a whole slew of KDE packages broke from there.  Swapping the nvidia-vdpau ppa that I had been using for thefirstm ppa solved the problem immediately.  I'm just hoping it will continue to work until the 190 driver becomes an official part of Karmic.

---

### Post by spamalam on 2009-11-16
Hey, I'm a bit lost here.  I managed to install the 190 drivers after a lot of fighting only to have them wiped when I upgraded.

Could someone help out a lowly peon with a bit more info?

The problem is exactly as described in the first post.  I need to upgrade to 190 and i need VDPAU for XBMC.

---

