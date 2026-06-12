---
title: "Update manager doesn't show anything to update"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by narnie on 2009-06-03
I am currently trying to resolve a problem on my sisters Ubuntu 8.04 installation.

She hasn't updated her Ubuntu install in several months, so I know there are MANY things to update. When I tried to do so for her, she had four relatively insignificant things to upgrade. I knew this wasn't enough. I was also expecting a significant upgrade to dansguardian.

I manually refreshed. Nothing.

I fired up Synaptic and reloaded. Then clicked Mark all Upgrades. Nothing was marked. Nothing to update.

In software sources, I ticked hardy-proposed and hardy-backports knowing this should result in bookoos of updates. Reloaded, and still nothing! Tried it in update manager, too. Said system up to date!

So, I go to a terminal. Run apt-get install update and apt-get install upgrade to see if there are any errors. There are none

This is the output:

```

woodnt@lynne-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
woodnt@lynne-desktop:~$ man apt-get
woodnt@lynne-desktop:~$ sudo apt-get update
[sudo] password for woodnt: 
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://archive.canonical.com hardy Release 
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg         
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Hit http://archive.canonical.com hardy Release 
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Ign http://archive.canonical.com hardy/partner Packages             
Ign http://archive.canonical.com hardy/partner Sources              
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://us.archive.ubuntu.com hardy-security Release             
Ign http://archive.canonical.com hardy/partner Packages             
Hit http://archive.canonical.com hardy/partner Packages             
Hit http://us.archive.ubuntu.com hardy/main Packages                
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://archive.canonical.com hardy/partner Sources
Hit http://archive.canonical.com hardy/partner Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/main Sources
Hit http://us.archive.ubuntu.com hardy-security/universe Sources
Hit http://us.archive.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy-security/multiverse Sources
Reading package lists... Done


woodnt@lynne-desktop:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have run update-manager from a terminal to capture any error codes, but found none.

Can anyone please tell me what is going on and how to resolved it.

With thanks,
Narnie

---

### Post by zvacet on 2009-06-05
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by narnie on 2009-06-06
Yep, had already done that, but it shows nothing to update. Please look at the code above where you see the results of doing a sudo apt-get upgrade/update.

---

### Post by mrtomservo on 2009-06-06
I don't think you really have a problem.  There probably aren't all that many updates for 8.04.  One thing you might want to try is to change the sources.list download location.  You can change this in synaptic.  You probably want to backup your existing sources.list just to be safe before making changes though.

---

### Post by Baelus on 2009-06-06
System -> Administration -> Synaptic Package Manager -> Settings -> Repositories

On the first tab is a drop-down list labeled "Download from:".

Select "Main Server" if it's not set already. That's probably your best bet.

Otherwise change it to a different location and try that.

---

