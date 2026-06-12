---
title: "GutsyUpgrades failed."
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by willou on 2009-02-23
Hello,

I've a server with Ubuntu 7.04 :

```

# cat /etc/issue
Ubuntu 7.04 \n \l


IP: 88.191.50.123
MAC: 00:40:63:e8:5e:09
INSTALL: 2008-04-11 18:42:00
HOSNAME: sd-8976

```

I've followed the documentation at this [URL]("https://help.ubuntu.com/community/GutsyUpgrades") but it doesn't worked for me.

I've updated my source.list : 

```

# cat /etc/apt/sources.list
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

I've checked that there's no other sources.list :

```

# ls -l /etc/apt/sources.list.d/
total 0

```

The update is in two steps, the first one : 

```

# aptitude install update-manager-core
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Reading state information... Fait       
Reading extended state information      
Initializing package states... Fait
Building tag database... Fait      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Fait

```

The last one : 

```

# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmpH1UQvo/gutsy.tar.gz'
authenticate '/tmp/tmpH1UQvo/gutsy.tar.gz' against '/tmp/tmpH1UQvo/gutsy.tar.gz.gpg' 

Lecture du cache

Vérification du gestionnaire de paquets
Reading package lists: Donecom feisty-backports/multiverse Packages: 98  
Reading state information: Done
Reading state information: Done
Reading state information: Done
Ignored http://fr.archive.ubuntu.com feisty-backports Release.gpg
Failed http://fr.archive.ubuntu.com feisty-backports Release.gpg
Ignored http://fr.archive.ubuntu.com feisty-backports Release
Failed http://fr.archive.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty Release.gpg
Done http://old-releases.ubuntu.com feisty-updates Release.gpg
Ignored http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Failed http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com feisty-security Release.gpg
Done http://old-releases.ubuntu.com feisty-backports Release.gpg
Hit http://old-releases.ubuntu.com feisty Release
Failed http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty-updates Release
Hit http://old-releases.ubuntu.com feisty-security Release
Hit http://old-releases.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty/main Packages
Done http://old-releases.ubuntu.com feisty-updates Release
Hit http://old-releases.ubuntu.com feisty/restricted Packages
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Done http://old-releases.ubuntu.com feisty-security Release
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Done http://old-releases.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Packages
Hit http://old-releases.ubuntu.com feisty-backports/restricted Packages
Hit http://old-releases.ubuntu.com feisty-backports/universe Packages
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Sources
Hit http://old-releases.ubuntu.com feisty-backports/restricted Sources
Hit http://old-releases.ubuntu.com feisty-backports/universe Sources
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Sources
Done downloading            
Ignored http://fr.archive.ubuntu.com feisty-backports Release.gpg
Failed http://fr.archive.ubuntu.com feisty-backports Release.gpg
Done http://old-releases.ubuntu.com feisty Release.gpg
Done http://old-releases.ubuntu.com feisty-updates Release.gpg
Done http://old-releases.ubuntu.com feisty-security Release.gpg
Done http://old-releases.ubuntu.com feisty-backports Release.gpg
Ignored http://fr.archive.ubuntu.com feisty-backports Release
Failed http://fr.archive.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty-updates Release
Hit http://old-releases.ubuntu.com feisty-security Release
Ignored http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Failed http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com feisty Release
Done http://old-releases.ubuntu.com feisty-updates Release
Hit http://old-releases.ubuntu.com feisty-backports Release
Failed http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com feisty-security Release
Done http://old-releases.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty/main Packages
Hit http://old-releases.ubuntu.com feisty/restricted Packages
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Packages
Hit http://old-releases.ubuntu.com feisty-backports/restricted Packages
Hit http://old-releases.ubuntu.com feisty-backports/universe Packages
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Sources
Hit http://old-releases.ubuntu.com feisty-backports/restricted Sources
Hit http://old-releases.ubuntu.com feisty-backports/universe Sources
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Sources
Done downloading            
Ignored http://fr.archive.ubuntu.com feisty-backports Release.gpg
Failed http://fr.archive.ubuntu.com feisty-backports Release.gpg
Done http://old-releases.ubuntu.com feisty Release.gpg
Done http://old-releases.ubuntu.com feisty-updates Release.gpg
Done http://old-releases.ubuntu.com feisty-security Release.gpg
Ignored http://fr.archive.ubuntu.com feisty-backports Release
Failed http://fr.archive.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-backports Release.gpg
Hit http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty-updates Release
Hit http://old-releases.ubuntu.com feisty-security Release
Ignored http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Failed http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com feisty Release
Done http://old-releases.ubuntu.com feisty-updates Release
Done http://old-releases.ubuntu.com feisty-security Release
Hit http://old-releases.ubuntu.com feisty-backports Release
Failed http://fr.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty/main Packages
Hit http://old-releases.ubuntu.com feisty/restricted Packages
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Packages
Hit http://old-releases.ubuntu.com feisty-backports/restricted Packages
Hit http://old-releases.ubuntu.com feisty-backports/universe Packages
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Sources
Hit http://old-releases.ubuntu.com feisty-backports/restricted Sources
Hit http://old-releases.ubuntu.com feisty-backports/universe Sources
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Sources
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Getting upgrade prerequisites failed
The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Restauration du système dans son état d'origine

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

The last step failed. In the log we can see the use of the fr.archive.ubuntu.com mirror that not exists in my sources.list. 

The update software add this mirror in a new file : 

```

# cat /etc/apt/sources.list.d/prerequists-sources.list 
# sources.list fragment for pre-requists (one with countrymirror, one fallback)
deb http://fr.archive.ubuntu.com/ubuntu feisty-backports main/debian-installer
#deb http://archive.ubuntu.com/ubuntu feisty-backports main/debian-installer
# below is just for testing
#deb http://archive.dogfood.launchpad.net/ubuntu feisty-backports main/debian-installer

```

How can I upgrade my old Ubuntu server installation ?

Thanks for your support.

David BOUCHÉ « Willou »
[http://www.willou.net](http://www.willou.net)

---

### Post by martc on 2009-02-23
hi there, 
 I had the same problem and I was told that some of the support for feisty is no longer available, so the upgrade to gutsy doesn't work. I just had to download a newer version ( hardy heron) to try and resolve some of my problems. Maybe thats the way to go for you as well. unless anyone knows of a different way to upgrade.

---

### Post by willou on 2009-02-23
I understand that the support for Feisty is no longer available, I can head it. But I really need to upgrade this server and I don't understand why the do-release add an old mirror that doesn't exist now. 

Does any one have an idea to upgrade my feisty ubuntu server ?

Thanks for your support.

---

### Post by forger on 2009-02-24
Bug #319146: [https://bugs.launchpad.net/bugs/319146](https://bugs.launchpad.net/bugs/319146)

> Note:
Upgrades with alternate CD *work* if you choose "No" to the question "Include latest updates from the Internet".

Alternate install cd:
32-bit: [http://releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-i386.iso](http://releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-i386.iso)
64-bit: [http://releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-amd64.iso](http://releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-amd64.iso)

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by willou on 2009-02-24
forger,

thanks for your answer but I want to upgrade a server, I can put a CD into this computer.

Do I can mount the ISO image in the remote server to do the trick ?
(Do you have an idea of how I can do that ?)

Thanks.

---

### Post by forger on 2009-02-24
Or the other way (**use at your own risk**!) is to just change the /etc/apt/sources.list from feisty  to hardy:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo sed -i 's/feisty/hardy/g' /etc/apt/sources.list
```

then update:
```

sudo aptitude update
sudo aptitude -y dist-upgrade
sudo reboot

```

After you reboot:
```

sudo aptitude update
sudo aptitude -y upgrade
```

---

### Post by willou on 2009-02-24
forger,

I can take too much risks for this server. 
I think I'll try to download and mount the iso image. 

Do you think it can work ?

Thanks.

---

### Post by forger on 2009-02-24
I've tested it on edgy and feisty to gutsy, which worked properly. I haven't tested it on servers though. Either way, I couldn't guarantee anything :(

If you don't have a graphical desktop manager (gnome/kde), try this:
```
sh /cdrom/cdromupgrade
```

instead of gksu "sh /cdrom/cdromupgrade"

Please have in mind that if it works, you **should upgrade** once more to hardy, or you'll have to go through this process all over again. :)

---

### Post by forger on 2009-02-24
> **willou said:**
> 
Do I can mount the ISO image in the remote server to do the trick ?
(Do you have an idea of how I can do that ?)


Please read the link:
[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by forger on 2009-02-24
By the way, it seems that you have misunderstood "use at your own risk". dist-upgrade is used for debian, but I don't believe that it will make any problems. aptitude (not apt-get) will resolve the dependencies properly!

I've just used ubuntu edgy server in a virtual machine and attempted to do this:

```
sudo sed -i 's/edgy/gutsy/g' /etc/apt/sources.list
```

But again, I can't give you any guarantees, YMMV (your mileage may vary). If it's super important, consult a tech person or the support team of your server.

This is how you update for feisty
```

sudo sed -i 's/feisty/gutsy/g' /etc/apt/sources.list
sudo aptitude update
sudo aptitude -y dist-upgrade

```

Let it finish. Once it starts installing, you might be asked a few questions, so be there when required. Usually you just hit enter, unless you have some custom configuration files you want to keep (Consult your tech support).

When it finishes:
```
sudo reboot
```
Note: You might be required to do this reboot through a web control panel (if you have one)

Then login and continue:
```

sudo aptitude update
sudo aptitude -y safe-upgrade
```

When that is done, attempt a full-upgrade to fix any dependencies left:
```
sudo aptitude update
sudo aptitude -y full-upgrade
```

---

### Post by forger on 2009-02-24
Once it finishes upgrading to gutsy, you can easily upgrade to hardy, which has 5 years support for servers:
```
sudo do-release-upgrade
```

---

### Post by mstephens on 2009-03-05
Anyone going from 7.04 to 7.10.

Adding the archived repositories to /etc/apt/sources.list only allows you to update 7.04 (i.e. stay at 7.04 but get the latest software patches for 7.04 ). In order for this to work you need to comment out ALL the lines in sources.list except for the ones you just added. (This and all the following manual steps need to be done as root - I did "**sudo sh**" at a terminal prompt to get a root command prompt before starting) 

Clicking on the 7.10 upgrade button in upgrade manager doesn't work even if 7.04 is fully up to date - you just get the "prerequisites" error message.

To upgrade to 7.10, uncomment all the lines you just commented out in sources.list and comment out (or delete) the ones you just added. Then change "**feisty**" to "**gutsy**" everywhere. I used gedit editor to do a find and replace but it doesn't matter how you do it.

At your root command prompt type

**aptitude update**
and let everything finish.
[ around 15 minutes for me]

then get type

**aptitude upgrade**

[ this will take several hours and you need to be around to answer prompts as they come up - for most of these just accept the default as generally they relate to changing configuration files and the default is to leave them as they were in 7.04 ]

After all this you should be at 7.10 Gutsy Gibbon and able to do any further updates/upgrades in the "normal" way.

I did all this on a VNC connection from a Windows laptop to the PC I was upgrading and it all worked without having to actually touch the PC (obviously I needed to reconnect after the various reboots but the PC is configured for auto-logon  )

So far the only issue I've found is that I needed to reconfigure sound to "auto-detect" in order to get some applications to work which had previously worked OK in 7.04. Everything else looks as it was including my customized open source video driver for the Radeon TV out card.

---

