---
title: "Kde4 install on Gutsy(7.10)"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by magawake on 2009-02-06
I am trying to install Kde4 on Gutsy.

Here is what I did:

Added 

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

```
apt-get update
apt-get install kde4-core 

```

Which gives me:
```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kde4-core: Depends: kdebase-runtime (>= 4:4.0.0) but it is not going to be installed
  kdebase-bin: Depends: kdebase-bin-kde3 but it is not going to be installed or
                        kdebase-runtime-bin-kde4 but it is not going to be installed
  kdebase-kde4: Depends: dolphin-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: kappfinder-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: kdebase-bin-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: kdebase-data-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: kdepasswd-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: kfind-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: konqueror-nsplugins-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: konqueror-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: konsole-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: kwrite-kde4 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
                Depends: libkonq5 (>= 4:4.0.3-0ubuntu2~gutsy1~ppa1) but it is not going to be installed
  kdebase-workspace-bin: Depends: kde-icons-oxygen but it is not going to be installed
                         Depends: kdebase-runtime but it is not going to be installed
                         Depends: kdebase-runtime-data but it is not going to be installed
  kdm-kde4: Depends: kde-icons-oxygen but it is not going to be installed
            Depends: kdebase-runtime but it is not going to be installed
            Depends: kdebase-runtime-data but it is not going to be installed
  klipper-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                Depends: kdebase-runtime but it is not going to be installed
                Depends: kdebase-runtime-data but it is not going to be installed
  ksysguard-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                  Depends: kdebase-runtime but it is not going to be installed
                  Depends: kdebase-runtime-data but it is not going to be installed
  kwin-kde4: Depends: kde-icons-oxygen but it is not going to be installed
             Depends: kdebase-runtime but it is not going to be installed
             Depends: kdebase-runtime-data but it is not going to be installed
  libplasma1: Depends: kde-icons-oxygen but it is not going to be installed
              Depends: kdebase-runtime but it is not going to be installed
              Depends: kdebase-runtime-data but it is not going to be installed
  systemsettings-kde4: Depends: kde-icons-oxygen but it is not going to be installed
                       Depends: kdebase-runtime but it is not going to be installed
                       Depends: kdebase-runtime-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Then I did:
```
root@ubuntu:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dolphin-kde4 kappfinder-kde4 kde-icons-oxygen kdebase-bin-kde4 kdebase-data-kde4 kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdepasswd-kde4 kfind-kde4 konqueror-kde4 konqueror-nsplugins-kde4 konsole-kde4
  kwrite-kde4 libkonq5
Recommended packages:
  xine-ui
The following NEW packages will be installed:
  dolphin-kde4 kappfinder-kde4 kde-icons-oxygen kdebase-bin-kde4 kdebase-data-kde4 kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdepasswd-kde4 kfind-kde4 konqueror-kde4 konqueror-nsplugins-kde4 konsole-kde4
  kwrite-kde4 libkonq5
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
59 not fully installed or removed.
Need to get 0B/55.7MB of archives.
After unpacking 89.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kde-icons-oxygen kdebase-runtime-data kdebase-runtime-bin-kde4 kdebase-runtime libkonq5 kfind-kde4 dolphin-kde4 kappfinder-kde4 kdebase-data-kde4 kdebase-bin-kde4 kdepasswd-kde4 konqueror-nsplugins-kde4 konqueror-kde4 konsole-kde4
  kwrite-kde4
Install these packages without verification [y/N]? y
(Reading database ... 162779 files and directories currently installed.)
Unpacking kde-icons-oxygen (from .../kde-icons-oxygen_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-icons-oxygen_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/oxygen/128x128/status/user-trash-full.png', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/dbus-1/interfaces/org.kde.KTimeZoned.xml', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-runtime-bin-kde4 (from .../kdebase-runtime-bin-kde4_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kstart', which is also in package kde4base
Unpacking kdebase-runtime (from .../kdebase-runtime_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/knotify4', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libkonq5 (from .../libkonq5_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libkonq5_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/kde4/konq_sound.so', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kfind-kde4 (from .../kfind-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kfind-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kfind', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking dolphin-kde4 (from .../dolphin-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/dolphin-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/dolphin', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kappfinder-kde4 (from .../kappfinder-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kappfinder-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kappfinder', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-data-kde4 (from .../kdebase-data-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-data-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/servicetypes/uasprovider.desktop', which is also in package kde4base-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdebase-bin-kde4 (from .../kdebase-bin-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-bin-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/keditfiletype', which is also in package kde4base
Unpacking kdepasswd-kde4 (from .../kdepasswd-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kdepasswd-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kdepasswd', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking konqueror-nsplugins-kde4 (from .../konqueror-nsplugins-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror-nsplugins-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/nspluginviewer', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking konqueror-kde4 (from .../konqueror-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kfmclient', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking konsole-kde4 (from .../konsole-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/konsole-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/konsoleprofile', which is also in package kde4base
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kwrite-kde4 (from .../kwrite-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kwrite-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/bin/kwrite', which is also in package kde4base
Errors were encountered while processing:
 /var/cache/apt/archives/kde-icons-oxygen_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_all.deb
 /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/kdebase-runtime_4%3a4.0.3-0ubuntu1~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/libkonq5_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/kfind-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/dolphin-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/kappfinder-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/kdebase-data-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_all.deb
 /var/cache/apt/archives/kdebase-bin-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/kdepasswd-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/konqueror-nsplugins-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/konqueror-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/konsole-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
 /var/cache/apt/archives/kwrite-kde4_4%3a4.0.3-0ubuntu2~gutsy1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Any ideas?

---

### Post by forger on 2009-02-07
The correct repo now is:
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu gutsy main
```

You can use this script to fix the ppa and get the GPG key:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

I don't think it will help you with your problem though.
Try sending a mail to the team:
[https://edge.launchpad.net/~kubuntu-members-kde4/+contactuser](https://edge.launchpad.net/~kubuntu-members-kde4/+contactuser)
or at the mailing list (address at [https://launchpad.net/~kubuntu-members-kde4](https://launchpad.net/~kubuntu-members-kde4) )

---

### Post by magawake on 2009-02-14
Ok. I managed to get it installed without any problems. I logged out and selected Kde4 as my session. I relogged in, but I get nothing back, just a black screen.

The system did not crash because I did a ctrl+alt+bkup to exit out. 

Any ideas? Do I need do anything else? 

dpkg -l | grep kde
```

rc  akregator                                  4:3.5.7enterprise20070926-0ubuntu2.1               RSS feed aggregator for KDE
rc  amor                                       4:3.5.8-0ubuntu1                                   a KDE creature for your desktop
rc  ark                                        4:3.5.8-0ubuntu1                                   graphical archiving tool for KDE
rc  atlantik                                   4:3.5.8-0ubuntu1                                   KDE client for Monopoly-like network games
rc  atlantikdesigner                           4:3.5.8-0ubuntu2                                   game board designer for Atlantik
rc  blinken                                    4:3.5.8-0ubuntu1                                   KDE version of the Simon Says electronic mem
ii  dolphin-kde4                               4:4.0.3-0ubuntu2~gutsy1~ppa1                       file manager for KDE 4 focusing on usability
rc  juk                                        4:3.5.8-0ubuntu1                                   music organizer and player for KDE
rc  kaboodle                                   4:3.5.8-0ubuntu1                                   light, embedded media player for KDE
rc  kaddressbook                               4:3.5.7enterprise20070926-0ubuntu2.1               KDE NG addressbook application
rc  kalarm                                     4:3.5.7enterprise20070926-0ubuntu2.1               KDE alarm message, command and email schedul
rc  kalzium                                    4:3.5.8-0ubuntu1                                   chemistry teaching tool for KDE
rc  kanagram                                   4:3.5.8-0ubuntu1                                   letter order game for KDE
rc  kandy                                      4:3.5.7enterprise20070926-0ubuntu2.1               KDE mobile phone utility
rc  kappfinder                                 4:3.5.8-2ubuntu3~gutsy1~ppa1                       non-KDE application finder for KDE
ii  kappfinder-kde4                            4:4.0.3-0ubuntu2~gutsy1~ppa1                       non-KDE application finder for KDE 4
rc  karm                                       4:3.5.7enterprise20070926-0ubuntu2.1               KDE time tracker tool
rc  kasteroids                                 4:3.5.8-0ubuntu1                                   Asteroids for KDE
rc  kate                                       4:3.5.8-2ubuntu3~gutsy1~ppa1                       advanced text editor for KDE
rc  katomic                                    4:3.5.8-0ubuntu1                                   Atomic Entertainment game for KDE
rc  kaudiocreator                              4:3.5.8-0ubuntu1                                   CD ripper and audio encoder frontend for KDE
rc  kbackgammon                                4:3.5.8-0ubuntu1                                   A Backgammon game for KDE
rc  kbattleship                                4:3.5.8-0ubuntu1                                   Battleship game for KDE
rc  kblackbox                                  4:3.5.8-0ubuntu1                                   A simple logical game for the KDE project
rc  kbruch                                     4:3.5.8-0ubuntu1                                   fraction calculation teaching tool for KDE
rc  kcalc                                      4:3.5.8-0ubuntu1                                   calculator for KDE
rc  kcharselect                                4:3.5.8-0ubuntu1                                   character selector for KDE
rc  kcontrol                                   4:3.5.8-2ubuntu3~gutsy1~ppa1                       control center for KDE
rc  kcron                                      4:3.5.8-0ubuntu1                                   the KDE crontab editor
rc  kdat                                       4:3.5.8-0ubuntu1                                   a KDE tape backup tool
ii  kde-icons-oxygen                           4:4.0.3-0ubuntu1~gutsy1~ppa1                       Oxygen icon theme for KDE4
ii  kde4-core                                  3.3~gutsy1~ppa1                                    the K Desktop Environment version 4 core mod
rc  kde4base                                   3.94.0-0ubuntu1                                    core applications for KDE 4 testing
ii  kde4libs-bin                               4:4.0.3-0ubuntu1~gutsy1~ppa1                       binaries for all the KDE 4 core applications
rc  kde4sdk                                    3.94.0-0ubuntu1                                    sdk applications for KDE 4 testing
rc  kdeartwork-theme-icon                      4:3.5.8-0ubuntu1                                   icon themes released with KDE
rc  kdebase-bin                                4:3.5.8-2ubuntu3~gutsy1~ppa1                       core binaries for the KDE base module
ii  kdebase-bin-kde4                           4:4.0.3-0ubuntu2~gutsy1~ppa1                       core binaries for the KDE 4 base module
ii  kdebase-data                               4:3.5.8-2ubuntu3~gutsy1~ppa1                       shared data files for the KDE base module
ii  kdebase-data-kde4                          4:4.0.3-0ubuntu2~gutsy1~ppa1                       shared data files for the KDE 4 base module
ii  kdebase-kde4                               4:4.0.3-0ubuntu2~gutsy1~ppa1                       base components from the official KDE 4 rele
rc  kdebase-kio-plugins                        4:3.5.8-2ubuntu3~gutsy1~ppa1                       core I/O slaves for KDE
ii  kdebase-runtime                            4:4.0.3-0ubuntu1~gutsy1~ppa1                       runtime components from the official KDE rel
ii  kdebase-runtime-bin-kde4                   4:4.0.3-0ubuntu1~gutsy1~ppa1                       KDE4 core binaries for the KDE base runtime 
ii  kdebase-runtime-data                       4:4.0.3-0ubuntu1~gutsy1~ppa1                       shared data files for the KDE base runtime m
ii  kdebase-workspace                          4:4.0.3-0ubuntu1~gutsy1~ppa3                       base components from the official KDE 4 rele
ii  kdebase-workspace-bin                      4:4.0.3-0ubuntu1~gutsy1~ppa3                       core binaries for the KDE 4 base module
ii  kdebase-workspace-data                     4:4.0.3-0ubuntu1~gutsy1~ppa3                       shared data files for the KDE 4 base module
ii  kdelibs-data                               4:3.5.8-0ubuntu3.4                                 core shared data for all KDE applications
ii  kdelibs4c2a                                4:3.5.8-0ubuntu3.4                                 core libraries and binaries for all KDE appl
ii  kdelibs5                                   4:4.0.3-0ubuntu1~gutsy1~ppa1                       core libraries for all KDE 4 applications
ii  kdelibs5-data                              4:4.0.3-0ubuntu1~gutsy1~ppa1                       core shared data for all KDE 4 applications
rc  kdelirc                                    4:3.5.8-0ubuntu1                                   infrared control for KDE
rc  kdemultimedia-kappfinder-data              4:3.5.8-0ubuntu1                                   multimedia data for kappfinder
rc  kdemultimedia-kio-plugins                  4:3.5.8-0ubuntu1                                   enables the browsing of audio CDs under Konq
rc  kdepasswd                                  4:3.5.8-2ubuntu3~gutsy1~ppa1                       password changer for KDE
ii  kdepasswd-kde4                             4:4.0.3-0ubuntu2~gutsy1~ppa1                       password changer for KDE 4
rc  kdepim-kresources                          4:3.5.7enterprise20070926-0ubuntu2.1               KDE pim resource plugins
rc  kdepim-wizards                             4:3.5.7enterprise20070926-0ubuntu2.1               KDE server configuration wizards
ii  kdepimlibs-data                            4:4.0.3-0ubuntu1~gutsy1~ppa1                       core shared data for KDE PIM 4 applications
ii  kdepimlibs5                                4:4.0.3-0ubuntu1~gutsy1~ppa1                       core libraries for KDE PIM 4 applications
rc  kdeprint                                   4:3.5.8-2ubuntu3~gutsy1~ppa1                       print system for KDE
rc  kdesktop                                   4:3.5.8-2ubuntu3~gutsy1~ppa1                       miscellaneous binaries and files for the KDE
rc  kdf                                        4:3.5.8-0ubuntu1                                   disk space utility for KDE
rc  kdict                                      4:3.5.8-0ubuntu2                                   dictionary client for KDE
ii  kdm-kde4                                   4:4.0.3-0ubuntu1~gutsy1~ppa3                       X display manager for KDE 4
rc  kdvi                                       4:3.5.8-0ubuntu1                                   dvi viewer for KDE
rc  kedit                                      4:3.5.8-0ubuntu1                                   basic text editor for KDE
rc  keduca                                     4:3.5.8-0ubuntu1                                   interactive form-based tests for KDE
rc  kenolaba                                   4:3.5.8-0ubuntu1                                   Enolaba board game for KDE
rc  kfax                                       4:3.5.8-0ubuntu1                                   G3/G4 fax viewer for KDE
rc  kfaxview                                   4:3.5.8-0ubuntu1                                   G3/G4 fax viewer for KDE using kviewshell
rc  kfilereplace                               4:3.5.8-0ubuntu1                                   batch search-and-replace component for KDE
rc  kfind                                      4:3.5.8-2ubuntu3~gutsy1~ppa1                       file-find utility for KDE
ii  kfind-kde4                                 4:4.0.3-0ubuntu2~gutsy1~ppa1                       file-find utility for KDE 4
rc  kfloppy                                    4:3.5.8-0ubuntu1                                   floppy formatter for KDE
rc  kfouleggs                                  4:3.5.8-0ubuntu1                                   A KDE clone of the Japanese PuyoPuyo game
rc  kgamma                                     4:3.5.8-0ubuntu1                                   gamma correction module for the KDE Control 
rc  kgeography                                 4:3.5.8-0ubuntu1                                   Geography learning tool for KDE
rc  kget                                       4:3.5.8-0ubuntu2                                   download manager for KDE
ii  kghostview                                 4:3.5.8-0ubuntu1                                   PostScript viewer for KDE
rc  kgoldrunner                                4:3.5.8-0ubuntu1                                   A KDE clone of the Loderunner arcade game
rc  kgpg                                       4:3.5.8-0ubuntu1                                   GnuPG frontend for KDE
rc  khangman                                   4:3.5.8-0ubuntu1                                   the classical hangman game for KDE
rc  khelpcenter                                4:3.5.8-2ubuntu3~gutsy1~ppa1                       help center for KDE
rc  khexedit                                   4:3.5.8-0ubuntu1                                   KDE hex editor
rc  kicker                                     4:3.5.8-2ubuntu3~gutsy1~ppa1                       desktop panel for KDE
rc  kicker-applets                             4:3.5.8-0ubuntu2                                   applets for Kicker, the KDE panel
rc  kiconedit                                  4:3.5.8-0ubuntu1                                   an icon editor for KDE
rc  kig                                        4:3.5.8-0ubuntu1                                   interactive geometry program for KDE
rc  kimagemapeditor                            4:3.5.8-0ubuntu1                                   HTML image map editor for KDE
rc  kiten                                      4:3.5.8-0ubuntu1                                   Japanese reference/study tool for KDE
rc  kjots                                      4:3.5.8-0ubuntu1                                   note taking utility for KDE
rc  kleopatra                                  4:3.5.7enterprise20070926-0ubuntu2.1               KDE Certificate Manager
rc  klettres                                   4:3.5.8-0ubuntu1                                   foreign alphabet tutor for KDE
rc  klickety                                   4:3.5.8-0ubuntu1                                   A Clickomania-like game for KDE
rc  klines                                     4:3.5.8-0ubuntu1                                   Color lines for KDE
rc  klinkstatus                                4:3.5.8-0ubuntu1                                   web link validity checker for KDE
rc  klipper                                    4:3.5.8-2ubuntu3~gutsy1~ppa1                       clipboard utility for KDE
ii  klipper-kde4                               4:4.0.3-0ubuntu1~gutsy1~ppa3                       clipboard utility for KDE 4
rc  kmag                                       4:3.5.8-0ubuntu1                                   a screen magnifier for KDE
rc  kmahjongg                                  4:3.5.8-0ubuntu1                                   the classic mahjongg game for KDE project
rc  kmail                                      4:3.5.7enterprise20070926-0ubuntu2.1               KDE Email client
rc  kmailcvt                                   4:3.5.7enterprise20070926-0ubuntu2.1               KDE KMail mail folder converter
rc  kmenuedit                                  4:3.5.8-2ubuntu3~gutsy1~ppa1                       menu editor for KDE
rc  kmid                                       4:3.5.8-0ubuntu1                                   MIDI/karaoke player for KDE
rc  kmilo                                      4:3.5.8-0ubuntu1                                   laptop special keys support for KDE
rc  kmines                                     4:3.5.8-0ubuntu1                                   Minesweeper for KDE
rc  kmix                                       4:3.5.8-0ubuntu1                                   sound mixer applet for KDE
rc  kmoon                                      4:3.5.8-0ubuntu1                                   moon phase indicator for KDE
rc  kmousetool                                 4:3.5.8-0ubuntu1                                   KDE mouse manipulation tool for the disabled
rc  kmouth                                     4:3.5.8-0ubuntu1                                   a type-and-say KDE frontend for speech synth
rc  kmplot                                     4:3.5.8-0ubuntu1                                   mathematical function plotter for KDE
rc  knetworkconf                               4:3.5.8-0ubuntu1                                   KDE network configuration tool
rc  knewsticker                                4:3.5.8-0ubuntu2                                   news ticker applet for KDE
rc  knode                                      4:3.5.7enterprise20070926-0ubuntu2.1               KDE news reader
rc  knotes                                     4:3.5.7enterprise20070926-0ubuntu2.1               KDE sticky notes
rc  kodo                                       4:3.5.8-0ubuntu1                                   mouse odometer for KDE
rc  kolf                                       4:3.5.8-0ubuntu1                                   Minigolf game for KDE
rc  kolourpaint                                4:3.5.8-0ubuntu1                                   a simple paint program for KDE
rc  konq-plugins                               4:3.5.8-0ubuntu2                                   plugins for Konqueror, the KDE file/web/doc 
rc  konqueror                                  4:3.5.8-2ubuntu3~gutsy1~ppa1                       KDE's advanced file manager, web browser and
ii  konqueror-kde4                             4:4.0.3-0ubuntu2~gutsy1~ppa1                       KDE 4's advanced file manager, web browser a
ii  konqueror-nsplugins-kde4                   4:4.0.3-0ubuntu2~gutsy1~ppa1                       Netscape plugin support for Konqueror
rc  konquest                                   4:3.5.8-0ubuntu1                                   KDE based GNU-Lactic Konquest game
ii  konsole                                    4:3.5.8-2ubuntu3~gutsy1~ppa1                       X terminal emulator for KDE
ii  konsole-kde4                               4:4.0.3-0ubuntu2~gutsy1~ppa1                       X terminal emulator for KDE 4
rc  konsolekalendar                            4:3.5.7enterprise20070926-0ubuntu2.1               KDE konsole personal organizer
rc  kontact                                    4:3.5.7enterprise20070926-0ubuntu2.1               KDE pim application
rc  kooka                                      4:3.5.8-0ubuntu1                                   scanner program for KDE
rc  kopete                                     4:3.5.8-0ubuntu2                                   instant messenger for KDE
rc  korganizer                                 4:3.5.7enterprise20070926-0ubuntu2.1               KDE personal organizer
rc  korn                                       4:3.5.7enterprise20070926-0ubuntu2.1               KDE mail checker
rc  kpackage                                   4:3.5.8-0ubuntu1                                   KDE package management tool
rc  kpager                                     4:3.5.8-2ubuntu3~gutsy1~ppa1                       desktop pager for KDE
rc  kpat                                       4:3.5.8-0ubuntu1                                   KDE solitaire patience game
ii  kpdf                                       4:3.5.8-0ubuntu1                                   PDF viewer for KDE
rc  kpercentage                                4:3.5.8-0ubuntu1                                   percentage calculation teaching tool for KDE
rc  kpersonalizer                              4:3.5.8-2ubuntu3~gutsy1~ppa1                       installation personalizer for KDE
rc  kpf                                        4:3.5.8-0ubuntu2                                   public fileserver for KDE
rc  kpilot                                     4:3.5.7enterprise20070926-0ubuntu2.1               KDE Palm Pilot hot-sync tool
rc  kpoker                                     4:3.5.8-0ubuntu1                                   KDE based Poker clone
rc  kppp                                       4:3.5.8-0ubuntu2                                   modem dialer and ppp frontend for KDE
rc  krdc                                       4:3.5.8-0ubuntu2                                   Remote Desktop Connection for KDE
rc  krec                                       4:3.5.8-0ubuntu1                                   sound recorder utility for KDE
rc  kreversi                                   4:3.5.8-0ubuntu1                                   Reversi for KDE
rc  krfb                                       4:3.5.8-0ubuntu2                                   Desktop Sharing for KDE
rc  ksame                                      4:3.5.8-0ubuntu1                                   SameGame for KDE
rc  ksayit                                     4:3.5.8-0ubuntu1                                   a frontend for the KDE Text-to-Speech system
rc  kscd                                       4:3.5.8-0ubuntu1                                   audio CD player for KDE
rc  kshisen                                    4:3.5.8-0ubuntu1                                   Shisen-Sho for KDE
rc  ksim                                       4:3.5.8-0ubuntu1                                   system information monitor for KDE
rc  ksirc                                      4:3.5.8-0ubuntu2                                   IRC client for KDE
rc  ksirtet                                    4:3.5.8-0ubuntu1                                   Tetris and Puyo-Puyo games for KDE
rc  ksmiletris                                 4:3.5.8-0ubuntu1                                   Tetris like game for KDE
rc  ksnake                                     4:3.5.8-0ubuntu1                                   Snake Race for KDE
rc  ksnapshot                                  4:3.5.8-0ubuntu1                                   screenshot utility for KDE
rc  ksokoban                                   4:3.5.8-0ubuntu1                                   Sokoban game for KDE
rc  kspaceduel                                 4:3.5.8-0ubuntu1                                   Arcade two-player space game for KDE
rc  ksplash                                    4:3.5.8-2ubuntu3~gutsy1~ppa1                       the KDE splash screen
rc  kstars                                     4:3.5.8-0ubuntu1                                   desktop planetarium for KDE
rc  ksvg                                       4:3.5.8-0ubuntu1                                   SVG viewer for KDE
rc  ksysguard                                  4:3.5.8-2ubuntu3~gutsy1~ppa1                       system guard for KDE
ii  ksysguard-kde4                             4:4.0.3-0ubuntu1~gutsy1~ppa3                       system guard for KDE 4
rc  ksysguardd                                 4:3.5.8-2ubuntu3~gutsy1~ppa1                       system guard daemon for KDE
ii  ksysguardd-kde4                            4:4.0.3-0ubuntu1~gutsy1~ppa3                       system guard daemon for KDE 4
rc  ksysv                                      4:3.5.8-0ubuntu1                                   KDE SysV-style init configuration editor
rc  kteatime                                   4:3.5.8-0ubuntu1                                   KDE utility for making a fine cup of tea
rc  ktimer                                     4:3.5.8-0ubuntu1                                   timer utility for KDE
rc  ktip                                       4:3.5.8-2ubuntu3~gutsy1~ppa1                       useful tips for KDE
rc  ktnef                                      4:3.5.7enterprise20070926-0ubuntu2.1               KDE TNEF viewer
rc  ktouch                                     4:3.5.8-0ubuntu1                                   touch typing tutor for KDE
rc  kttsd                                      4:3.5.8-0ubuntu1                                   a Text-to-Speech system for KDE
rc  ktuberling                                 4:3.5.8-0ubuntu1                                   Potato Guy for KDE
rc  ktux                                       4:3.5.8-0ubuntu1                                   Tux screensaver for KDE
rc  kuser                                      4:3.5.8-0ubuntu1                                   KDE user/group administration tool
rc  kverbos                                    4:3.5.8-0ubuntu1                                   Spanish verb form study application for KDE
rc  kview                                      4:3.5.8-0ubuntu1                                   simple image viewer/converter for KDE
rc  kvoctrain                                  4:3.5.8-0ubuntu1                                   vocabulary trainer for KDE
rc  kwalletmanager                             4:3.5.8-0ubuntu1                                   wallet manager for KDE
rc  kweather                                   4:3.5.8-0ubuntu1                                   weather display applet for KDE
rc  kwifimanager                               4:3.5.8-0ubuntu2                                   wireless lan manager for KDE
ii  kwin                                       4:3.5.8-2ubuntu3~gutsy1~ppa1                       the KDE window manager
ii  kwin-kde4                                  4:4.0.3-0ubuntu1~gutsy1~ppa3                       the KDE 4 window manager
rc  kwin4                                      4:3.5.8-0ubuntu1                                   Connect Four clone for KDE
rc  kworldclock                                4:3.5.8-0ubuntu1                                   earth watcher for KDE
ii  kwrite-kde4                                4:4.0.3-0ubuntu2~gutsy1~ppa1                       text editor for KDE 4
rc  kxsldbg                                    4:3.5.8-0ubuntu1                                   graphical XSLT debugger for KDE
rc  libindex0                                  4:3.5.7enterprise20070926-0ubuntu2.1               KDE indexing library
rc  libkcal2b                                  4:3.5.7enterprise20070926-0ubuntu2.1               KDE calendaring library
rc  libkcddb1                                  4:3.5.8-0ubuntu1                                   CDDB library for KDE
rc  libkdeedu3                                 4:3.5.8-0ubuntu1                                   library for use with KDE educational apps
rc  libkdegames1                               4:3.5.8-0ubuntu1                                   KDE games library and common files
rc  libkdepim1a                                4:3.5.7enterprise20070926-0ubuntu2.1               KDE PIM library
rc  libkgantt0                                 4:3.5.7enterprise20070926-0ubuntu2.1               KDE gantt charting library
rc  libkleopatra1                              4:3.5.7enterprise20070926-0ubuntu2.1               KDE GnuPG interface libraries
rc  libkmime2                                  4:3.5.7enterprise20070926-0ubuntu2.1               KDE MIME interface library
ii  libkonq5                                   4:4.0.3-0ubuntu2~gutsy1~ppa1                       core libraries for KDE 4's Konqueror
ii  libkonq5-templates                         4:4.0.3-0ubuntu2~gutsy1~ppa1                       data files needed by core libraries for KDE 
rc  libkpimexchange1                           4:3.5.7enterprise20070926-0ubuntu2.1               KDE PIM Exchange library
rc  libkpimidentities1                         4:3.5.7enterprise20070926-0ubuntu2.1               KDE PIM user identity information library
rc  libkscan1                                  4:3.5.8-0ubuntu1                                   scanner library for KDE
rc  libksieve0                                 4:3.5.7enterprise20070926-0ubuntu2.1               KDE mail/news message filtering library
rc  liblockdev1                                1.0.3-1.2build1                                    Run-time shared library for locking devices
rc  libmimelib1c2a                             4:3.5.7enterprise20070926-0ubuntu2.1               KDE mime library
ii  libplasma1                                 4:4.0.3-0ubuntu1~gutsy1~ppa3                       library for the plasma KDE 4 desktop
ii  libqimageblitz4                            0.0.706674-2build1                                 KDE/Qt image filter library
rc  librss1                                    4:3.5.8-0ubuntu2                                   RSS library for KDE
rc  lskat                                      4:3.5.8-0ubuntu1                                   Lieutnant Skat card game for KDE
rc  networkstatus                              4:3.5.7enterprise20070926-0ubuntu2.1               KDE network status monitor
rc  noatun                                     4:3.5.8-0ubuntu1                                   media player for KDE
rc  noatun-plugins                             4:3.5.8-0ubuntu2                                   plugins for Noatun, the KDE media player
rc  quanta                                     4:3.5.8-0ubuntu1                                   web development environment for KDE
ii  systemsettings-kde4                        4:4.0.3-0ubuntu1~gutsy1~ppa3                       KDE 4 System Settings Center

any ideas?


```

---

### Post by theozzlives on 2009-02-14
Can't believe you put KDE4 on Gutsy :lolflag:

---

### Post by magawake on 2009-02-14
Its possible. 

I would upgrade, but I don't like the new inittab of Ubuntu. 7.10 is really nice.

If I can't get the dpkg I may as well compile Kde 4.2 on it.

---

