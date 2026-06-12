---
title: "[SOLVED] Update failure"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by joshh88 on 2009-01-11
For the past week the updater has been trying to install 73 files. Every time thought it has the same error. I'm sorry I would search it but I'm having to hand write it and type it, so for convenience sake I am posting here anew. 
*Exact Words of Error*

Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release](http://archive.canonical.com/ubuntu/dists/gutsy/Release)
Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file(malformed release file?)
Some index files failed to download, they have been ignored, or old ones are used instead:confused:

---

### Post by joshh88 on 2009-01-12
BUMP no ideas

---

### Post by taurus on 2009-01-12
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by joshh88 on 2009-01-12
I'm at work so I'll have that posted as soon as I get home

---

### Post by joshh88 on 2009-01-12
Ok here you go josh@josh-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823.5)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy universe
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy multiverse
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial

deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security universe
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) hardy-security multiverse
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823.5)]/ gutsy main restricted

---

### Post by taurus on 2009-01-12
You have four gutsy's repos mixing in with hardy.  It's not a good idea to mix repos like that in your /etc/apt/sources.list.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the repos for gutsy to comment them out.

```

**[COLOR="Blue"]#[/COLOR]**deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
**[COLOR="Blue"]#[/COLOR]**deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
**[COLOR="Blue"]#[/COLOR]**deb http://archive.canonical.com/ubuntu gutsy commercial
**[COLOR="Blue"]#[/COLOR]**deb-src http://archive.canonical.com/ubuntu gutsy commercial

```
Save it and exit gedit editing window.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by joshh88 on 2009-01-12
Is there a way to save or do you just exit the window and start a new one?

---

### Post by taurus on 2009-01-12
There is an option, blue arrow above a harddrive icon, to save it in gedit.  If you place a cursor over it, you would see the text "Save the current file."

Otherwise, click File -> Save.

---

### Post by joshh88 on 2009-01-12
Nevermind lol just tried it and realized it opened in another window not terminal

---

### Post by joshh88 on 2009-01-12
when i try sudo apt-get update or up grade it says this 

josh@josh-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823.5) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823.5) gutsy/restricted Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy Release.gpg                     
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/main Translation-en_US          
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/universe Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/multiverse Translation-en_US
Get:1 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/universe Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/multiverse Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security Release.gpg
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/main Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/restricted Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/universe Translation-en_US
Ign [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/multiverse Translation-en_US
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                      
Get:2 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates Release [58.5kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security Release
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/main Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/restricted Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/restricted Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/main Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/multiverse Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/universe Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/universe Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy/multiverse Packages
Get:3 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main Packages [406kB]
Get:4 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/restricted Packages [8001B]
Get:5 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/restricted Sources [903B]
Get:6 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/main Sources [105kB]
Get:7 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/multiverse Sources [4601B]
Get:8 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/universe Sources [34.7kB]
Get:9 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/universe Packages [155kB]
Get:10 [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-updates/multiverse Packages [26.4kB]
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/main Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/restricted Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/restricted Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/main Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/multiverse Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/universe Sources
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/universe Packages
Hit [http://ubuntu.mirror.frontiernet.net](http://ubuntu.mirror.frontiernet.net) hardy-security/multiverse Packages
Fetched 800kB in 5s (145kB/s)                  
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823.5) gutsy/main Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Alpha%20i386%20(20070823.5)_dists_gutsy_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823.5) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Alpha%20i386%20(20070823.5)_dists_gutsy_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
josh@josh-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by joshh88 on 2009-01-12
op I think I got it... sudo apt-get update; just like ti told me to lol. I'm bad at now listening thank you very uch Taurus

---

