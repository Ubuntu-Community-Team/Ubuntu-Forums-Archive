---
title: "apt-get update gives &quot;Sub-process gzip returned an error code (1)"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by ceabaird on 2009-03-24
Having a problem getting apt-get to update. I get the following result when I use:

sudo apt-get update

> gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                                                 
  Sub-process gzip returned an error code (1)
Fetched 222kB in 2min18s (1599B/s)                                                                           
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

My /etc/apt/sources.list file looks like this:

> #
# deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) sarge main
deb-src [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) sarge main

I tried removing any partial files from /var/lib/apt/lists/partial with this command:

sudo rm /var/lib/apt/lists/partial/*

which did clean out a file, but after that, trying to run apt-get update returned the same Failed message as above. I also tried using:

sudo wget [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)

but it keeps stalling and stops. Where do I need to look from here?

---

### Post by spcwingo on 2009-03-24
Have you tried:

```
sudo apt-get install --reinstall gzip
```

---

### Post by ceabaird on 2009-03-24
sudo apt-get install --reinstall gzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 101kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main gzip 1.3.12-3.2 [101kB]
Fetched 101kB in 1s (61.5kB/s)
(Reading database ... 47490 files and directories currently installed.)
Preparing to replace gzip 1.3.12-3.2 (using .../gzip_1.3.12-3.2_i386.deb) ...
Unpacking replacement gzip ...
Setting up gzip (1.3.12-3.2) ...

and then I ran:

sudo rm /var/lib/apt/lists/partial/*

re-ran sudo apt-get update, and this is where it keeps hanging:

> Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [426kB]
69% [1 Packages 296569/426kB 69%]

then returned this:

> Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [426kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources                                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [553kB]                                       
56% [2 Packages gzip 0]                                                             47.6kB/s 49710d 6h28min8s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                                                 
  Sub-process gzip returned an error code (1)
Fetched 257kB in 2min18s (1847B/s)                                                                           
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.
  

Is there something else I could try?

---

### Post by spcwingo on 2009-03-24
Maybe your apt cache is full.  Try:

```
sudo apt-get clean && sudo apt-get update
```

If that doesn't work try selecting a different server in synaptic.  If all else fails try changing the offending source in /etc/apt/sources.list from http:// to ftp://

---

### Post by ceabaird on 2009-03-25
OK, I wasn't able to get synaptic to download. I did a silly thing, which was try to upgrade to 8.10 (since I thought the LTS version was out), and ended up not being able to install 8.10 successfully, and down-graded back to 8.04.2 by going into /etc/apt/sources.list and changing all the "intrepid" callouts to "hardy" - then doing:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

it "appears" to be working...

---

### Post by ceabaird on 2009-03-25
I cleaned up my /etc/apt/sources.list:

> # newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

 and tried to do the update - but I am getting this error:
> 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [553kB]                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                                                      
  Connection failed [IP: 91.189.88.40 80]
Fetched 8191B in 4min16s (32B/s) 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 91.189.88.40 80]

Since I'm running a server here, I don't have access to any GUI repository managers, so how can I change the repositories in terminal, if that seems to be the best way to over come the above issue.

One more questions is which part of the sources.list should I change from http:// to ftp:// ? I'm not quite sure which line refers to:

> [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages 

Would this be the first 2 lines in sources.list?
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

Thanks for your help with this, much appreciated!

---

### Post by spcwingo on 2009-03-25
> **ceabaird said:**
> down-graded back to 8.04.2 by going into /etc/apt/sources.list and changing all the "intrepid" callouts to "hardy"

This is most likely the problem.  More than likely your install is hosed.  I hope for your sake that it is not.  Unfortunately, I cannot help further.  Hopefully someone with more experience in these matters will drop by soon.

---

### Post by ceabaird on 2009-04-06
It looks like this is the section that it chokes on:

> Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1105B] 

---

