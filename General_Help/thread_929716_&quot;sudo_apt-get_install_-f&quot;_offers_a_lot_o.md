---
title: "&quot;sudo apt-get install -f&quot; offers a lot of packages to remove - what to do?"
date: 2008-09-25
forum: General Help
---

### Post by _irRa on 2008-09-25
Hi,
I've got the Adept refusing to install (any) packages and suggesting me to do "sudo apt-get install -f", 
which results in HUGE amount of seem-to-be important packages being offered for removal (I refuse).
 
I've got the Kubuntu Gutsy (7.10) system and I have it (or it has me, dunno ;)) without the network (have not yet installed it properly under kubuntu - was in the process),
so I'm downloading packages from the Internet manually, using other machine, and then try to install them one by one, then, if the downloaded packages need other packages, I download and install them also, etc
(stupid/boring temporary process, but it worked for most of the cases).

So,  after trying to install (n such a way) one of the packages which requested a password, 
(it was either libenchant1c2a_1.3.0-3_i386.deb or python2.5-minimal_2.5.1-5ubuntu5.2_i386.deb will need to look into /var/log/dpkg.log file - as I recently learned)
the install was not finished and the adept started to say (for any package)
"Broken dependencies
Your system has broken dependencies. This application can not continue untill this is fixed. To fix it run 'sudo synaptic' or 'sudo apt-get install -f' in a terminal window",

After I launced "sudo apt-get install -f" the system the system listed a lot of packages as "needed to remove" and offered to do it.
I refused and have not yet launched the process - since the list of packages is suspiciously long and includes important packages (see full list in the message below).

I've searched the net and find the following:
[LIST]
[*]records of similar cases when some other users have launched it (+ become frightened and interrupted the process :)) and resulted in backup-reinstall activities (see [http://ubuntuforums.org/showthread.php?t=655519](http://ubuntuforums.org/showthread.php?t=655519))
[*]general info pages on APT (like its official manual [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/))
[/LIST]

Both are for sure interesting and I've/'ll read (at least some parts) of them,
but the great thing (for me and for other people with same problem searching for "sudo apt-get install -f" :)) to be obtained now
is the couple of simple advices from someone experienced (and having time :)) on what to do:
[LIST=1]
[*] To not (occasionally) ruin their system/data (e.g. during reinstallation network distributives can be unreacheble, so... or you may loose data if ...)
[*] To choose the easiest/best back-up/restore track (e.g. is it possible to come back to some, I don't know, restore point instead of massively reinstalling? )
[*] To avoid/be prepared for such situations in the future (e.g. not to install single pakages, if not beeing abs. sure in ... and they are ...) or (e.g. use back-up - restore point software like ...)
[/LIST]

Thanks in advance for your answers!
 (unfortunately cannot try them immediately - since kubuntu is my homesystem - so will try them in the evening then I'll came home)

Sorry for beeing wordy, newby, and "brain -f"y,
_irRa

---

### Post by _irRa on 2008-09-25
comment: the system messages were translated to English

> Reading lists of packages... Finished
Building the tree of dependencies
Reading state information... Finished
Fixing the dependencies... Finished
Packages to be REVOMED:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater akregator alsa-utils amarok amarok-xine apport apport-qt ark
  command-not-found digikam dolphin gdebi-core gdebi-kde guidance-backends
  gwenview hplip hplip-gui hwdb-client-common hwdb-client-kde k3b kaddressbook
  kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron
  kde-guidance kde-guidance-powermanager kde-style-polyester
  kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins
  kdebluetooth kdegraphics-kfile-plugins kdelibs4c2a
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources
  kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview
  khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper
  kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base
  kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror
  konqueror-nsplugins konsole kontact konversation kooka kopete korganizer
  kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash
  ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent
  kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal
  language-selector-common language-selector-qt language-support-en
  launchpad-integration libk3b2 libk3b2-mp3 libkbluetooth0 libkcal2b libkcddb1
  libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  libpythonize0 libskim0 lsb-release network-manager-kde networkstatus
  openoffice.org-help-en-us openoffice.org-kde openoffice.org-writer
  pykdeextensions python python-apport python-apt python-central python-dbus
  python-gnupginterface python-kde3 python-launchpad-bugs python-libxml2
  python-problem-report python-qt3 python-qt4 python-qt4-dbus python-sip4
  python-software-properties python-support python-uno python-xdg python2.5
  python2.5-dev rdiff-backup restricted-manager-core restricted-manager-kde
  scim-qtimm skim software-properties-kde strigi-applet
  thunderbird-locale-en-gb ubuntu-minimal unattended-upgrades
  update-manager-core xorg
updated 0, installed 0 new packages, for removal marked  73 packages, and 0 packages not updated.
Necessary to download 0B of archives.
After depackaging volume of free space will be decreased by 574MB.
Would you like to continue [Y/n]? n
Emergency exit.
irra@isay:~$


---

