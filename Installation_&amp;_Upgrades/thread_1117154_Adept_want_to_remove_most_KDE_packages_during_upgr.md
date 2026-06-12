---
title: "Adept want to remove most KDE packages during upgrade"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by nusch on 2009-04-05
I have Kubuntu 8.10. There appeared as always once a week update notifier in tray. But from some reason adepts wants to remove most KDE base packages i.e Doplhin, kmix, klipper, kate,  kubuntu-desktop. Raw apt-get upgrade also gives me:
```

nusch@novopad:~$ sudo apt-get upgrade
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci
Odczyt informacji o stanie... Gotowe
Nast&#281;puj&#261;ce pakiety zosta&#322;y zatrzymane:[stopped]
  akregator ark dolphin dragonplayer gwenview kaddressbook kalarm kamera kate kbugbuster kcalc kde-window-manager kde-zeroconf kdebase-bin
  kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards
  kdepimlibs5 kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool kmouth kmplot knotes kompare konqueror konqueror-nsplugins konsole
  kontact kopete korganizer krdc krfb ksnapshot ksysguard ktimetracker kttsd kwalletmanager libkcddb4 libkdecorations4 libkdepim4
  libkholidays4 libkleo4 libkonq5 libkpgp4 libksieve4 libkwineffects1 libmimelib4 libokularcore1 okteta okular okular-extra-backends
  python-kde4 superkaramba systemsettings
Nast&#281;puj&#261;ce pakiety zostan&#261; zaktualizowane:[upgraded]
  kde-icons-oxygen kde-printer-applet kdebase-runtime-data kdebase-runtime-data-common kdelibs5-data kdepimlibs-data ksysguardd
  libkonq5-templates libphonon4 libsoprano4 phonon phonon-backend-xine soprano-daemon
13 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 72 nieaktualizowanych.
Konieczne pobranie 24,1MB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 1737kB miejsca na dysku.
Kontynuowa&#263; [T/n]?

```

I don't know if its known error in kubuntu or one of third party packages, here is my apt sources list:
```

nusch@novopad:/etc/apt$ cat sources.list                                                                                                     
# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted                                            
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to                                                                    
# newer versions of the distribution.                                                                                                        

deb http://pl.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://pl.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid universe               
# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid multiverse              
# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://pl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://apt.wxwidgets.org/ gutsy-wx main
deb http://ppa.launchpad.net/patryk-prezu/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
deb http://dl.google.com/linux/deb/ testing non-free


```

---

### Post by twent4 on 2009-04-06
Got the same issue, just reposted it about 23 hours ago.
*BUMP*

edit:
just got it fixed, comment out *deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main* in /etc/apt/souces.list, run **apt-get update**

---

