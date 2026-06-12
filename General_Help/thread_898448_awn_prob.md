---
title: "awn prob"
date: 2008-08-23
forum: General Help
---

### Post by perlsyntax on 2008-08-23
How do i make my awn to work and how do i make sure it the only panel when i start up my pc?


i went here [http://wiki.awn-project.org/FAQ](http://wiki.awn-project.org/FAQ)



i still have some prob understand it.

---

### Post by borobudur on 2008-08-23
I did this and no problem with it:
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```Here I got my info from: [http://ubuntuforums.org/showthread.php?t=385981&highlight=Avant+Window+Navigator](http://ubuntuforums.org/showthread.php?t=385981&highlight=Avant+Window+Navigator)

---

### Post by perlsyntax on 2008-08-23
i get this error


perlsyntax@perlsyntax-desktop:~$ sudo bash
[sudo] password for perlsyntax: 
root@perlsyntax-desktop:~# sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr
root@perlsyntax-desktop:~# apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multivers Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  multivers/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@perlsyntax-desktop:~# sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr
root@perlsyntax-desktop:~#

---

### Post by borobudur on 2008-08-23
Supposing you have Gutsy 7.10, did you add necessary repositories?

I did this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories)

---

### Post by perlsyntax on 2008-08-23
i have 8.04

---

### Post by borobudur on 2008-08-23
What I did in Hardy is that I replaced from the suggested list the country code and the Ubuntu version. In my case: us. -> ch. and gutsy -> hardy
That worked in my case, perhaps try without changing the country code, might just take a bit longer.

You do a backup before so nothing can happen:
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```

---

### Post by perlsyntax on 2008-08-23
i re install my unbuntu and now i get this message


root@csyntax-desktop:~# sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr

---

### Post by borobudur on 2008-08-23
I checked my Hardy machine, there I found this in the list:

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```Just add it to the /etc/apt/sources.list file (don't forget the backup) and update (sudo apt-get update). 

If I think about it, I suppose you need also the Compiz package (very nice eye candy stuff):
```
sudo apt-get install emerald
```Play around with it, config over System -> Preferences -> Emerald Themes Manager After

then do this if you don't see any change:
```
emerald --replace
```

---

### Post by borobudur on 2008-09-25
What happened??

---

