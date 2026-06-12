---
title: "apt-get cant download &amp; ubdates etc give errors"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Rex Regis on 2009-02-13
I am totally new to to Linux having come across from vista.  I am using Ubuntu hardy 8.04.1.  I tried to follow some instructions for installing software via apt-get and every time I try, no matter what it is, I get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager


 this was having put the following command into the terminal:

~$ sudo apt-get install compizconfig-settings-manager

I also tried other packages and got the same result.

Then when I try to reload Synaptic Package Manager  I get the following message:

Could not download all repository indexes

GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: NODATA 2Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  302 Moved Temporarily
Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  302 Moved Temporarily
Some index files failed to download, they have been ignored, or old ones used instead.



The internet works fine.  can anyone help me please?!

---

### Post by avtolle on 2009-02-13
The lines that generated the 404 errors are for Feisty, which has reached its end of life; edit your /etc/apt/sources.list and comment them out. To edit, go to Applications>Accessories>Terminal, and do```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list
```to open the file for editing. When done, Ctrl+o to write, enter to accept the file name, Ctrl+x to exit. The first command was to make a backup file, just in case.

On the other errors, once the editing is complete, try again; it looks like there's a temporary fix going on with the server.

---

### Post by Rex Regis on 2009-02-13
Thanks for such a quick response!  After following your instructions the situation remains unchanged.  I had something different when I tried to install the awn dock.  I put this in:

~$ sudo aptitude install avant-window-navigator-bzr awn-core-applets-bzr


and got this back (but the program does not seem to be installed):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "avant-window-navigator-bzr"
Couldn't find any package whose name or description matched "awn-core-applets-bzr"
Couldn't find any package whose name or description matched "avant-window-navigator-bzr"
Couldn't find any package whose name or description matched "awn-core-applets-bzr"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   


Thanks for your help!

---

### Post by avtolle on 2009-02-13
Have you seen [http://ubuntuforums.org/showthread.php?t=975231?](http://ubuntuforums.org/showthread.php?t=975231?) It seems to me that awn is in the repos as "awn" (w/o the quotes).

---

### Post by Rex Regis on 2009-02-13
I followed the instructions on this page.  There was lots of activity, especialy with the update command, but in the end everything failed. The result of the update looked like this:
```

Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Get:1 http://archive.canonical.com hardy Release.gpg [189B]                    
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Packages                               
99% [Connecting to archive.ubuntu-rocks.org] [Waiting for headers] [Waiting for
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Get:3 http://archive.canonical.com hardy Release [6998B]                       
Ign http://archive.canonical.com hardy Release                             
Ign http://download.tuxfamily.org feisty Release.gpg                 
Hit http://archive.canonical.com hardy/partner Packages
Ign http://archive.ubuntu-rocks.org hardy Release.gpg
Hit http://archive.canonical.com hardy/partner Sources
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Ign http://archive.ubuntu-rocks.org hardy/main Translation-en_US
Ign http://download.tuxfamily.org feisty Release                               
Ign http://archive.ubuntu-rocks.org hardy/restricted Translation-en_US         
Ign http://download.tuxfamily.org feisty/avant-window-navigator Packages
Ign http://archive.ubuntu-rocks.org hardy/universe Translation-en_US
Ign http://download.tuxfamily.org feisty/avant-window-navigator Sources        
Ign http://archive.ubuntu-rocks.org hardy/multiverse Translation-en_US         
Err http://download.tuxfamily.org feisty/avant-window-navigator Packages       
  404 Not Found
Err http://download.tuxfamily.org feisty/avant-window-navigator Sources        
  404 Not Found
Ign http://archive.ubuntu-rocks.org hardy-updates Release.gpg
Ign http://archive.ubuntu-rocks.org hardy-updates/main Translation-en_US       
Ign http://archive.ubuntu-rocks.org hardy-updates/restricted Translation-en_US 
Ign http://archive.ubuntu-rocks.org hardy-updates/universe Translation-en_US   
Ign http://archive.ubuntu-rocks.org hardy-updates/multiverse Translation-en_US 
Ign http://archive.ubuntu-rocks.org hardy-security Release.gpg                 
Ign http://archive.ubuntu-rocks.org hardy-security/main Translation-en_US      
Ign http://archive.ubuntu-rocks.org hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu-rocks.org hardy-security/universe Translation-en_US  
Ign http://archive.ubuntu-rocks.org hardy-security/multiverse Translation-en_US
Ign http://archive.ubuntu-rocks.org hardy Release           
Ign http://archive.ubuntu-rocks.org hardy-updates Release
Ign http://archive.ubuntu-rocks.org hardy-security Release  
Ign http://archive.ubuntu-rocks.org hardy/main Packages     
Ign http://archive.ubuntu-rocks.org hardy/restricted Packages
Ign http://archive.ubuntu-rocks.org hardy/universe Packages
Ign http://archive.ubuntu-rocks.org hardy/multiverse Packages
Ign http://archive.ubuntu-rocks.org hardy-updates/main Packages
Ign http://archive.ubuntu-rocks.org hardy-updates/restricted Packages
Ign http://archive.ubuntu-rocks.org hardy-updates/universe Packages
Ign http://archive.ubuntu-rocks.org hardy-updates/multiverse Packages
Ign http://archive.ubuntu-rocks.org hardy-security/main Packages
Ign http://archive.ubuntu-rocks.org hardy-security/restricted Packages
Ign http://archive.ubuntu-rocks.org hardy-security/universe Packages
Ign http://archive.ubuntu-rocks.org hardy-security/multiverse Packages
Err http://archive.ubuntu-rocks.org hardy/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy/universe Packages 
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy/multiverse Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-updates/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-updates/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-updates/universe Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-updates/multiverse Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-security/main Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-security/restricted Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-security/universe Packages
  302 Moved Temporarily
Err http://archive.ubuntu-rocks.org hardy-security/multiverse Packages
  302 Moved Temporarily
Fetched 191B in 1min16s (3B/s)
W: GPG error: http://archive.canonical.com hardy Release: The following signatures were invalid: NODATA 2
W: Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz  404 Not Found

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  302 Moved Temporarily

W: Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  302 Moved Temporarily

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Then on install awn:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: python-gnome2-extras but it is not installable
E: Broken packages
```

---

### Post by Dougie187 on 2009-02-13
Why don't you post your /etc/apt/sources.list file so we can check that out.

---

### Post by Rex Regis on 2009-02-13
when I put that into the terminal

```
bash: /etc/apt/sources.list: Permission denied
```

---

### Post by Rex Regis on 2009-02-13
ok, sorry guys, have just sorted the problem.  this is the sources.list file:

```
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu-rocks.org/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy universe
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy multiverse
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-security universe
deb http://archive.ubuntu-rocks.org/ubuntu/ hardy-security multiverse

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

I hope this helps!

---

### Post by Rex Regis on 2009-02-13
that is, I have solved the 'permission denied' problem, not the original one.:???:

---

### Post by forger on 2009-02-14
> Address Not Found
Firefox can't find the server at archive.ubuntu-rocks.org.
[http://archive.ubuntu-rocks.org/](http://archive.ubuntu-rocks.org/)

You have to use another server.

I've fixed it for you and added you the default archive.ubuntu.com server, you have to execute this in terminal:
```
sudo wget http://pastebin.ca/raw/1337073 -O /etc/apt/sources.list
sudo apt-get update
sudo apt-get -y upgrade
```

---

### Post by nexus86 on 2009-02-14
Hi guys, new to linux, awesome so far :D

First major problem of mine, would appreciate assistance.

I connect through DHCP at work, we also have a server called aptcache.fundamo.com which caches packages so that all the packages we DL from the internet gets stored there for faster retrieval etc etc. So I am able to DL packages from work.

Now, at home I share my internet connection from my XP box using ICS and my ubuntu box is able to use it as a gateway to connect to the internet. I assign a static IP for my ubuntu LAN connection.

I do have internet access through the gateway so that is not the problem.

My problem is that id I do sudo apt-get update, ubuntu still wants to use my work proxy aptcache.fundamo.com to get packages from.

The interesting thing is, if I go to network proxy settings, there is no aptcache.fundamo.com there. I also dis a search for aptcache.fundamo.com in my file system and did not find any references to it.

here is my problem:

 sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'aptcache.fundamo.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'aptcache.fundamo.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems



here is my sources list :


# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

any help would be epic thx

---

### Post by linux_tech on 2009-02-14
If you want updates by apt or aptitude to use a http proxy, you can type
```

    export http_proxy=http://user:password@proxy:port/

    or

    export http_proxy=http://proxy:port/


```

---

### Post by nexus86 on 2009-02-14
Thx for reply, but if you read my post, that is not what I want to do.

I just want to be able to get/update packages from the internet directly without using a proxy, the problem is it still wants to use aptcache.fundamo.com as a proxy when I am at HOME, but I do not have that proxy defined in my network proxy settings, so I cant figuere out why my system wants to use that proxy and where it reads it from...

any ideas?
thx

---

### Post by Rex Regis on 2009-02-14
Thanks, forger, for your help. It has fixed some things.  apt-get doesn't work but if I replace the code 'apt-get' (from a tutorial) with 'aptitude' then it seems to work.  update manager informed me that there was an upgrade to v. 8.10.  So I did that.  Unfortunately, the process only reaches the second stage "Setting new software channels" and then gives the error "Error authenticating some packages" and then gives a very long list of names. The only option then is to close it down.  Do you have any ideas?](*,)

---

### Post by forger on 2009-02-14
ok, try execute these commands now:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 FBB75451
```
```
gpg --export -a 437D05B5 | sudo apt-key add -
```
```
gpg --export -a FBB75451 | sudo apt-key add -
```

And then execute these:
```
sudo apt-key net-update
sudo apt-get update
sudo apt-get -y upgrade
```

Post the output of the last three

---

### Post by Rex Regis on 2009-02-14
so "sudo apt-key net-update" returned nothing.

sudo apt-get update returned:

```
Get:1 http://archive.ubuntu.com hardy Release.gpg [189B]
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:2 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Get:3 http://archive.canonical.com hardy Release.gpg [189B]                    
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://download.tuxfamily.org feisty Release.gpg                           
Get:4 http://archive.canonical.com hardy Release [6998B]                       
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://archive.canonical.com hardy Release                                 
Get:5 http://archive.canonical.com hardy/partner Packages [4127B]              
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Get:6 http://archive.canonical.com hardy/partner Sources [1598B]               
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Get:7 http://archive.ubuntu.com hardy-updates Release.gpg [189B]               
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://download.tuxfamily.org feisty Release                               
Get:8 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://download.tuxfamily.org feisty/avant-window-navigator Packages       
Ign http://ppa.launchpad.net hardy/main Packages                     
Get:9 http://ppa.launchpad.net hardy/main Packages [1738B]           
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://download.tuxfamily.org feisty/avant-window-navigator Sources
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Err http://download.tuxfamily.org feisty/avant-window-navigator Packages
  404 Not Found
Err http://download.tuxfamily.org feisty/avant-window-navigator Sources
  404 Not Found
Get:10 http://security.ubuntu.com hardy-security Release [58.5kB]
Ign http://security.ubuntu.com hardy-security Release
Get:11 http://security.ubuntu.com hardy-security/main Packages [118kB]
Get:12 http://security.ubuntu.com hardy-security/restricted Packages [7487B]   
Get:13 http://security.ubuntu.com hardy-security/universe Packages [56.1kB]    
Get:14 http://security.ubuntu.com hardy-security/multiverse Packages [11.3kB]  
Get:15 http://archive.ubuntu.com hardy Release [65.9kB]                        
Ign http://archive.ubuntu.com hardy Release                                  
Get:16 http://archive.ubuntu.com hardy-updates Release [58.5kB]              
Ign http://archive.ubuntu.com hardy-updates Release                          
Get:17 http://archive.ubuntu.com hardy/main Packages [1178kB]                
Get:18 http://archive.ubuntu.com hardy/restricted Packages [6986B]         
Get:19 http://archive.ubuntu.com hardy/universe Packages [4293kB]          
Get:20 http://archive.ubuntu.com hardy/multiverse Packages [179kB]             
Get:21 http://archive.ubuntu.com hardy-updates/main Packages [420kB]           
Get:22 http://archive.ubuntu.com hardy-updates/restricted Packages [8001B]     
Get:23 http://archive.ubuntu.com hardy-updates/universe Packages [165kB]       
Get:24 http://archive.ubuntu.com hardy-updates/multiverse Packages [27.7kB]    
Fetched 6697kB in 12s (542kB/s)                                                
W: GPG error: http://archive.canonical.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: NODATA 2
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

sudo apt-get -y upgrade returned:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by forger on 2009-02-14
Try this now, I've disabled the cd rom and the extra repositories:

```

ping -c 5 archive.ubuntu.com
ping -c 5 security.ubuntu.com
sudo wget http://pastebin.ca/raw/1337218 -O /etc/apt/sources.list
sudo apt-get update
sudo apt-get clean
sudo apt-get update

```

post the output again :)

---

### Post by Rex Regis on 2009-02-14
ping -c 5 archive.ubuntu.com:

```
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=1 ttl=45 time=165 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=2 ttl=45 time=162 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=3 ttl=45 time=164 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=4 ttl=45 time=171 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=5 ttl=45 time=160 ms

--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 160.600/164.863/171.525/3.679 ms
```

ping -c 5 security.ubuntu.com:

```
PING security.ubuntu.com (91.189.88.37) 56(84) bytes of data.
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=1 ttl=44 time=161 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=2 ttl=44 time=164 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=3 ttl=44 time=236 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=4 ttl=44 time=247 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=5 ttl=44 time=258 ms

--- security.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 161.148/213.538/258.235/41.994 ms
```

sudo wget [http://pastebin.ca/raw/1337218](http://pastebin.ca/raw/1337218) -O /etc/apt/sources.list:
```

--13:22:49--  http://pastebin.ca/raw/1337218
           => `/etc/apt/sources.list'
Resolving pastebin.ca... 208.68.18.97
Connecting to pastebin.ca|208.68.18.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,693 (2.6K) [text/plain]

100%[====================================>] 2,693         --.--K/s             

13:23:00 (1.59 MB/s) - `/etc/apt/sources.list' saved [2693/2693]
```

sudo apt-get update:

```
Get:1 http://archive.ubuntu.com hardy Release.gpg [189B]
Get:2 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Get:3 http://archive.canonical.com hardy Release.gpg [189B]                    
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Get:4 http://archive.canonical.com hardy Release [6998B]                       
Ign http://archive.canonical.com hardy Release                                 
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://archive.canonical.com hardy/partner Sources                         
Get:5 http://archive.ubuntu.com hardy-updates Release.gpg [189B]
Get:6 http://security.ubuntu.com hardy-security Release [58.5kB]           
Ign http://security.ubuntu.com hardy-security Release                      
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Packages
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security/restricted Packages
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US      
Hit http://security.ubuntu.com hardy-security/universe Packages             
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://security.ubuntu.com hardy-security/multiverse Packages           
Get:7 http://archive.ubuntu.com hardy Release [65.9kB]
Ign http://archive.ubuntu.com hardy Release                                 
Get:8 http://archive.ubuntu.com hardy-updates Release [58.5kB]              
Ign http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Get:9 http://archive.ubuntu.com hardy-updates/main Packages [420kB]
Get:10 http://archive.ubuntu.com hardy-updates/restricted Packages [8001B]     
Get:11 http://archive.ubuntu.com hardy-updates/universe Packages [167kB]       
Get:12 http://archive.ubuntu.com hardy-updates/multiverse Packages [27.7kB]    
Fetched 682kB in 7s (85.8kB/s)                                                 
Reading package lists... Done
W: GPG error: http://archive.canonical.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: NODATA 2
W: You may want to run apt-get update to correct these problems
```

sudo apt-get clean:

NO RESPONSE

sudo apt-get update:

```
Get:1 http://archive.canonical.com hardy Release.gpg [189B]
Get:2 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Get:3 http://archive.ubuntu.com hardy Release.gpg [189B]                       
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Get:5 http://archive.canonical.com hardy Release [6998B]                       
Ign http://archive.canonical.com hardy Release                                 
Get:6 http://security.ubuntu.com hardy-security Release [58.5kB]     
Ign http://security.ubuntu.com hardy-security Release                 
Get:7 http://archive.ubuntu.com hardy Release [65.9kB]                
Ign http://archive.ubuntu.com hardy Release                                    
Get:8 http://archive.ubuntu.com hardy-updates Release [58.5kB]                 
Ign http://archive.ubuntu.com hardy-updates Release                          
Hit http://archive.canonical.com hardy/partner Packages               
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://security.ubuntu.com hardy-security/universe Packages            
Hit http://archive.ubuntu.com hardy/universe Packages                      
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Fetched 761B in 1s (644B/s)                          
Reading package lists... Done
W: GPG error: http://archive.canonical.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: NODATA 2
W: You may want to run apt-get update to correct these problems
```

---

### Post by forger on 2009-02-14
Is this a normal Ubuntu or is it a derivative? Where did you download this Ubuntu? from [www.ubuntu.com](www.ubuntu.com) or another site?
Can you post the output of:
```
lsb_release -a
cat /etc/issue
```


OK, this will be a bit more aggressive, it will clear all the apt source lists and archives:
**[COLOR="Red"]USE CAREFULLY AND AT YOUR OWN RISK![/COLOR]**
```

sudo rm -f /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
sudo rm -f /var/lib/apt/lists/* /var/lib/apt/lists/partial/*
sudo rm -f /var/lib/apt/mirrors/* /var/lib/apt/mirrors/partial/*
sudo dpkg-reconfigure apt
sudo aptitude update

```

---

### Post by forger on 2009-02-14
Can you also post the output of:
```
apt-config dump
dpkg -l *apt*

```

---

### Post by Rex Regis on 2009-02-14
apt-config dump:

```
APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "0";
APT::Install-Suggests "0";
APT::Acquire "";
APT::Acquire::Translation "environment";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT::Install-Recommends-Sections "";
APT::Install-Recommends-Sections:: "metapackages";
APT::Install-Recommends-Sections:: "restricted/metapackages";
APT::Install-Recommends-Sections:: "universe/metapackages";
APT::Install-Recommends-Sections:: "multiverse/metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Update "";
APT::Update::Post-Invoke-Success "";
APT::Update::Post-Invoke-Success:::: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu hardy-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";
```

dpkg -l *apt*:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  apt            0.7.9ubuntu17. Advanced front-end for dpkg
un  apt-doc        <none>         (no description available)
ii  apt-utils      0.7.9ubuntu17. APT utility programs
ii  aptitude       0.4.9-2ubuntu5 terminal-based package manager
un  aptitude-doc   <none>         (no description available)
un  aptitude-doc-e <none>         (no description available)
ii  apturl         0.2.2ubuntu1   Install package with the apt protocol
un  gnome-apt      <none>         (no description available)
un  gsynaptic      <none>         (no description available)
un  gsynaptics     <none>         (no description available)
un  ksynaptics     <none>         (no description available)
ii  laptop-detect  0.13.2ubuntu1  attempt to detect a laptop
ii  laptop-mode-to 1.35-1ubuntu1  Scripts to spin down hard drive and save pow
un  libapt-inst-li <none>         (no description available)
un  libapt-pkg-dev <none>         (no description available)
un  libapt-pkg-doc <none>         (no description available)
un  libapt-pkg-lib <none>         (no description available)
ii  python-apt     0.7.4ubuntu7.4 Python interface to libapt-pkg
un  python-apt-dbg <none>         (no description available)
un  python2.3-apt  <none>         (no description available)
un  python2.4-apt  <none>         (no description available)
un  python2.5-apt  <none>         (no description available)
un  qsynaptics     <none>         (no description available)
ii  synaptic       0.61ubuntu9    Graphical package manager
un  xfree86-driver <none>         (no description available)
un  xorg-driver-sy <none>         (no description available)
ii  xserver-xorg-i 0.14.7~git2007 Synaptics TouchPad driver for X.Org server
```

also, apt-get seems to be working now, but still the same problem with updating the distro etc

---

### Post by forger on 2009-02-14
What do you mean? apt-get does not show any errors now?
What kind of problem do you have with the distro?

---

### Post by Rex Regis on 2009-02-14
apt-get was refusing to do anything for me.  every time I put in a command it would give me:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package
```

I was doing exact cut-&-paste from tutorials on web pages.  Since then I have been doing the things that other people have told me to do on this forum.  then shortly before I told you that apt-get was working, suddenly it started to download the packages, using the exact same commands that I had been giving it before.  So that is what  mean by apt-get is now working.:)

The thing about the distro update is that the update manager informs me that there is an upgrade to v. 8.10 and offers to do it for me.  it goes through the motions to the second phase "setting new software channels" and then gives the error: "Error authenticating some packages" and a long list of packages.  I get a similar message when I click "check" on the update manager.  It goes through the motions of downloading package info, and then returns the error "An error occured" with the following details:

```
following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: NODATA 2
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 2
```

I hope that this helps.:P

---

### Post by forger on 2009-02-14
1) Maybe this error, "NODATA 2", is a server error that disappears after a couple of "sudo apt-get update" commands.

2) Use the alternate cd to upgrade to 8.10: [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)
Choose "PC (Intel x86) alternate install CD" for 32-bit or "64-bit PC (AMD64) alternate install CD" for 64-bit.

Then follow instructions at: [http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

3) Despite (2), I would suggest a clean install using the desktop cd.
Things to know:
- You will have to get familiar with partitioning.
- Backup your important data, e.g. your home folder
- I recommend virtual machines such as [www.virtualbox.org](www.virtualbox.org) to play around and learn how to partition your drive properly :)

---

### Post by Rex Regis on 2009-02-14
Thanks a lot for all your help.  the apt-get update over and over doesn't do anything.  However, the alternate install cd is just what I was looking for!  I tried to update via CD already, but with the regular ubuntu iso...needless to say it didn't work, but this should be good...

wish me luck. :-o

---

### Post by forger on 2009-02-15
good luck! :)
By the way, with the alternate cd, when it asks you to update through internet select "no", this will probably help a bit, as it won't check for internet updates (you will do them later).

---

### Post by Rex Regis on 2009-02-16
OK it didn't work.  I have downloaded the install iso for v.8.10 and have installed but the same problem!  I am going to continue trying to seek help, but I will start a new thread since I am now using a different version of the os from the original post.

---

### Post by trepid666 on 2009-02-16
Have you tried opening Applications ---> Add/remove and enabling third party software? that might help

---

### Post by Rex Regis on 2009-02-16
I dont see any option to enable third party software in the Add/Remove.  When I set the drop-down to show third party software it shows nothing and says that there are no matching applications available.  I have however checked both options in *system* > *Administration* > *Software Sources* and the *Third Party Software* tab.

---

