---
title: "KDE 4.2 won't install properly on ubuntu 8.10?"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by totallyclueless on 2009-04-11
I'm using Ubuntu 8.10 and I can't seem to install Kubuntu 4.2

[http://news.softpedia.com/news/How-to-Install-KDE-4-2-on-Ubuntu-8-10-106118.shtml](http://news.softpedia.com/news/How-to-Install-KDE-4-2-on-Ubuntu-8-10-106118.shtml)

I got up to "Step 2 - Install KDE 4.2" and when I clicked the link to download, it says:
 "Can not install 'kubuntu-desktop' (E:Unable to correct problems, you have held broken packages.)"

I thought by deleting all of my kdeb-blahblha files on my synaptic program
but i still get the samething.

What's going on?

---

### Post by taurus on 2009-04-11
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by totallyclueless on 2009-04-11
> **taurus said:**
> Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
sarah@sarah-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex
deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
sarah@sarah-desktop:~$

---

### Post by abn91c on 2009-04-11
the softpedia guide is a bit outdated, go to [http://www.kubuntu.org](http://www.kubuntu.org) and follow the official guide there. the warning in Red(in the softpedia guide)about konqueror is partially true. the solution if it occurs in your PC is to change the home page in settings>configure konqueror>when konqueror starts" to anything from "show introduction page" or in other words change the default home page.
and by the way change your repositories to the Main or US servers, I have seen many posts here of users having problems with the Canadian servers.

---

### Post by totallyclueless on 2009-04-12
> **abn91c said:**
> the softpedia guide is a bit outdated, go to [http://www.kubuntu.org](http://www.kubuntu.org) and follow the official guide there. the warning in Red(in the softpedia guide)about konqueror is partially true. the solution if it occurs in your PC is to change the home page in settings>configure konqueror>when konqueror starts" to anything from "show introduction page" or in other words change the default home page.
and by the way change your repositories to the Main or US servers, I have seen many posts here of users having problems with the Canadian servers.
Hey, um, I actually don't really understand anything your talking about. Haha
My username says it all. I literally am a beginner at this.
Do you mind telling me step by step?
btw, I don't have a konquerer and don't know how to change my server :(

---

### Post by taurus on 2009-04-12
What happens if you run these commands from a terminal, one at a time?

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by totallyclueless on 2009-04-13
> **taurus said:**
> What happens if you run these commands from a terminal, one at a time?

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
sarah@sarah-desktop:~$ sudo apt-get update
[sudo] password for sarah: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_CA        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_CA  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_CA  
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA [3750B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg                  
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Translation-en_CA [2731B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA [3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Translation-en_CA   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_CA                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Sources     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Sources   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_CA
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Fetched 10.2kB in 18s (544B/s)
Reading package lists... Done
sarah@sarah-desktop:~$ sudo apt-get install kubuntu-desktop
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
                   Recommends: plasmoid-quickaccess but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: update-notifier-kde but it is not going to be installed
E: Broken packages
sarah@sarah-desktop:~$

---

### Post by abn91c on 2009-04-13
open **adept** package manager change your repositories location(click on the kubuntu software tab) there then follow the guide here [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)
see attached Pic

---

