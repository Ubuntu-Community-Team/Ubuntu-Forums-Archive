---
title: "update manager problem in jaunty"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by clueless dave on 2009-08-20
After upgrading to jaunty, I've started having problems with update manager - specifically it's never done a complete update.  Instead it tells me it can't authenticate certain programs, offers a partial upgrade, and then returns programs that still can't be updated/upgraded (consistently gnome-dbg, syslinux and syslinux-common).  

Here's the output of sudo apt-get update:

$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Get:1 [http://ftp.us.debian.org](http://ftp.us.debian.org) lenny Release.gpg [1032B]             
Ign [http://ftp.us.debian.org](http://ftp.us.debian.org) lenny/main Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg
Get:2 [http://ftp.us.debian.org](http://ftp.us.debian.org) lenny Release [73.6kB]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://ftp.us.debian.org](http://ftp.us.debian.org) lenny Release                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Hit [http://ftp.us.debian.org](http://ftp.us.debian.org) lenny/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Sources
Fetched 1033B in 0s (1183B/s)
Reading package lists... Done
W: GPG error: [http://ftp.us.debian.org](http://ftp.us.debian.org) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY 4D270D06F42584E6
W: You may want to run apt-get update to correct these problems

I love the helpful suggestion to run update AGAIN! (doesn't do any good, by the way).


Here's the output of cat /etc/apt/sources.list - 

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) lenny main


At first I thought maybe the lenny main item was a problem, but it's probably needed for the debian stuff - although the hangup every time  is failure to get gnome-dbg, syslinux and syslinux-common....

Any ideas?  Thanks.

---

### Post by zvacet on 2009-08-20
You have mixed repos and that is not recommended but if you want to keep it that way then type in terminal

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  9AA38DCD55BE302B
gpg --export --armor   9AA38DCD55BE302B| sudo apt-key add -

```

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  4D270D06F42584E6
gpg --export --armor  4D270D06F42584E6 | sudo apt-key add -

```

After first command hit enter.When you are finish do 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by clueless dave on 2009-08-20
What do you mean by mixed repos, and what would I change to follow good practice?

---

### Post by zvacet on 2009-08-21
> What do you mean by mixed repos

I mean that you have Ubuntu and Debian repos in your source list.If that works for you continue with it.It is your comp after all.

---

### Post by clueless dave on 2009-08-21
Thanks very much.  I don't recall how the debian repository was included in the list, but I didn't care that it was there (or not) unless there was some reason to have it there.  Long story short, I commented out the line referencing that repo and everything's working fine.  (I'm reminded I need more practice with vi!).  Thanks again.

---

