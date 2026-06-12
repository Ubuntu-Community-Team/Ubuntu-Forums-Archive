---
title: "Packages have been kept back / dist-upgrade likely to break system"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Aristide on 2009-04-03
Hi,
Running Kubuntu 8.10 / KDE 4.1.4 on Dell Optiplex.
When I started an apt-get upgrade, I suddenly got this :
---
[INDENT][I]The following packages have been kept back:
  akregator ark dolphin dragonplayer gwenview kaddressbook kamera kate kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5 kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konsole kontact kopete korganizer krdc krfb ksnapshot ksysguard ktimetracker kwalletmanager libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkleo4 libkonq5 libkpgp4 libksieve4 libkwineffects1 libmimelib4 libokularcore1 okular okular-extra-backends python-kde4 systemsettings
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.
[/INDENT][/I]---
On the forum, I repeatedly found the suggestion to do a sudo apt-get dist-upgrade, so I entered the command. To my amazement the console showed me that major and essential packages are going to be removed and nothing points to the fact that they would be replaced. Looking at what it says, this will break my entire system :
---
[INDENT][I]The following packages will be REMOVED:
  adept akregator amarok-kde4 ark digikam-doc dolphin dragonplayer gdebi-kde guidance-power-manager gwenview install-package jockey-kde kaddressbook kamera kate kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin kdebase-workspace-libs4+5 kdebluetooth kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdeplasma- ddons kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer krdc krfb ksnapshot ksysguard ksystemlog ktimetracker ktorrent kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi5 libkleo4 libkonq5 libkpgp4 libksieve4 libkwineffects1 libmimelib4 libokularcore1 libplasma2 okular okular-extra-backends plasmoid-quickaccess python-kde4 rosegarden software-properties-kde systemsettings update-manager-kde update-notifier-kde
The following NEW packages will be installed:
  akonadi-server libdbd-mysql-perl libdbi-perl libical0 libmeanwhile1 libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-server-5.0
The following packages have been kept back:
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdepimlibs5
The following packages will be upgraded:
  kdebase-workspace-data
1 upgraded, 9 newly installed, 87 to remove and 4 not upgraded.
[/I]---
[/INDENT]How did I get into this situation and more importantly, how can I rectify it without compromising my system ?
Thanks for any reply !

---

### Post by steevc on 2009-04-03
That looks something like what I had today. I let today's update run and it removed most of KDE. Luckily I could still run xfce to get some work done.

I'm now trying to get KDE working again, but have a clash between packages

E: /var/cache/apt/archives/kdebase-workspace-data_4%3a4.1.4-0ubuntu1~intrepid3.1_all.deb: trying to overwrite `/usr/share/kde4/apps/desktoptheme/default/colors', which is also in package kdebase-runtime-data

I'm looking for a solution.

---

### Post by Aristide on 2009-04-04
Continued - experiments so far :
I just fetched my Kubuntu 8.10 notebook from the office just to compare what's in /etc/apt.
The difference that stands out is that my desktop pc contains this line :
*http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu*
where my notebook does not (it has an out-of-the-box Kubuntu install without anything else yet).
I don't know how this line got into my desktop pc sources.list, perhaps because it contains a lot more software, notably multimedia and stuff and I might have had to add it somehow.

Now for the interesting part :
I removed the ppa.launchpad.net line from /etc/apt/sources.list
Then I executed apt-get update + upgrade + dist-upgrade
Resulting in this :

[I]sudo apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US                                                 
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US                                           
Hit http://archive.canonical.com intrepid Release.gpg                                                                    
Ign http://archive.canonical.com intrepid/partner Translation-en_US                                                      
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US                                              
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US                                            
Hit http://packages.medibuntu.org intrepid Release.gpg                                                                   
Ign http://packages.medibuntu.org intrepid/free Translation-en_US                                                        
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US                                                    
Hit http://security.ubuntu.com intrepid-security Release                                                                 
Hit http://be.archive.ubuntu.com intrepid Release.gpg                                                                    
Ign http://be.archive.ubuntu.com intrepid/main Translation-en_US                                                         
Hit http://archive.canonical.com intrepid Release                                                                        
Ign http://be.archive.ubuntu.com intrepid/restricted Translation-en_US                                                   
Ign http://be.archive.ubuntu.com intrepid/universe Translation-en_US                                                     
Ign http://be.archive.ubuntu.com intrepid/multiverse Translation-en_US                                                   
Hit http://be.archive.ubuntu.com intrepid-updates Release.gpg                                                            
Ign http://be.archive.ubuntu.com intrepid-updates/main Translation-en_US                                                 
Ign http://be.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://be.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://packages.medibuntu.org intrepid Release
Hit http://archive.canonical.com intrepid/partner Packages
Ign http://be.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://be.archive.ubuntu.com intrepid Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://be.archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://be.archive.ubuntu.com intrepid/main Packages
Hit http://be.archive.ubuntu.com intrepid/restricted Packages
Hit http://be.archive.ubuntu.com intrepid/main Sources
Hit http://be.archive.ubuntu.com intrepid/restricted Sources
Hit http://be.archive.ubuntu.com intrepid/universe Packages
Hit http://be.archive.ubuntu.com intrepid/universe Sources
Hit http://be.archive.ubuntu.com intrepid/multiverse Packages
Hit http://be.archive.ubuntu.com intrepid/multiverse Sources
Hit http://packages.medibuntu.org intrepid/non-free Packages
Hit http://be.archive.ubuntu.com intrepid-updates/main Packages
Hit http://be.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://be.archive.ubuntu.com intrepid-updates/main Sources
Hit http://be.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://be.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://be.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://be.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://be.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/I]
Not one error. However, many of my applications probably don't get upgraded like this anymore (see my first post).
So the misery definitely comes from the ppa.launchpad.net repository.
Adding this information, does anyone see the light (while I keep searching, too) ?

---

### Post by swizec on 2009-04-04
I had the same problem and my solution was to add teh kubuntu-experimental repository.

Then I had to manually apt-get several things like kate, amarok, kopete etc. to get everything working near perfectly with kde4.2

The only thing I'm still missing are the folderview plasmoids and in plasmoid config the dropdowns don't seem to work so I can't set up the weather widgets.

If anyone has any idea what package folderview plasmoids are in I'd be most grateful to find out since they were rather essential to how I organised my desktop.

---

### Post by CyberMando on 2009-04-04
I think you should give serious consideration to upgrading to Jaunty. It has been quite stable for a few weeks now and has a very nice KDE4.2.2 setup. I think I have fewer upgrade issues than I have seen in Intrepid.

---

### Post by Aristide on 2009-04-06
> **CyberMando said:**
> I think you should give serious consideration to upgrading to Jaunty. It has been quite stable for a few weeks now and has a very nice KDE4.2.2 setup. I think I have fewer upgrade issues than I have seen in Intrepid.

I think I'll go with your solution CyberMando.
I have already tested it on my notebook, which has a pretty basic Kubuntu out-of-the-box setup. Apart from a CUPS error after the upgrade (don't remember which one), everything went well. On my desktop, I'll take a backup and a mirror before proceeding.
In the mean time, some people that I have converted to Kubuntu over the last year, have proceeded with their apt-get dist-upgrade and had their entire system broken. I'm dealing with their furious phonecalls now, while I'm preparing my escape to Columbia, or some place.
I can understand their anger. It's also pretty much a first, in 29 years of computing, that I see an upgrade procedure withdrawing vital software from a system, making it unusable.
The whole matter will not pull me away from Kubuntu, but will do for some of my 'convertees' and eventually has put a stop to my Kubuntu aficionado-ism for the time being.
Anyway, looking forward to some KDE 4.2.2-happiness now !  It looks great on my notebook.

-----------------
Added 20.IV.2009
The upgrade procedure quit just after downloading, and broke my APT system.
Not being able to fix this, I'll need to fresh-install.
Waiting for the final release.

---

