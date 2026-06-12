---
title: "apt-get problems help please?"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by jtskinner on 2008-12-21
I looked around I can't find anything to help me solve this problem I have with apt-get.

When I try to install a package, let's just use wine as an example I get this:
jts@jts-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  jikes libsablevm-native1 jikes-sablevm libsablevm-classlib1-java
Use 'apt-get autoremove' to remove them.
Suggested packages:
  msttcorefonts xdg-utils
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9807kB of archives.
After unpacking, 45.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe wine 0.9.33-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.33-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.33-0ubuntu1_i386.deb) 404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

So then I obviously try to update and get this:
jts@jts-laptop:~$ sudo apt-get update
Password:
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release.gpg
  Could not resolve 'apt.cerkinfo.be'
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Translation-en_CA
  Could not resolve 'apt.cerkinfo.be'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Translation-en_CA
  Could not resolve 'apt.cerkinfo.be'
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources  
Ign [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Ign [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Ign [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Packages        
  Could not resolve 'apt.cerkinfo.be'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages   
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Packages
  Could not resolve 'apt.cerkinfo.be'
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Sources
  Could not resolve 'apt.cerkinfo.be'
Err [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Sources
  Could not resolve 'apt.cerkinfo.be'
Fetched 2B in 2s (1B/s)            
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/Release.gpg](http://apt.cerkinfo.be/dists/unstable/Release.gpg) Could not resolve 'apt.cerkinfo.be'
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/main/i18n/Translation-en_CA.bz2](http://apt.cerkinfo.be/dists/unstable/main/i18n/Translation-en_CA.bz2) Could not resolve 'apt.cerkinfo.be'
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/contrib/i18n/Translation-en_CA.bz2](http://apt.cerkinfo.be/dists/unstable/contrib/i18n/Translation-en_CA.bz2) Could not resolve 'apt.cerkinfo.be'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/main/binary-i386/Packages.gz](http://apt.cerkinfo.be/dists/unstable/main/binary-i386/Packages.gz) Could not resolve 'apt.cerkinfo.be'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/contrib/binary-i386/Packages.gz](http://apt.cerkinfo.be/dists/unstable/contrib/binary-i386/Packages.gz) Could not resolve 'apt.cerkinfo.be'
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/main/source/Sources.gz](http://apt.cerkinfo.be/dists/unstable/main/source/Sources.gz) Could not resolve 'apt.cerkinfo.be'
Failed to fetch [http://apt.cerkinfo.be/dists/unstable/contrib/source/Sources.gz](http://apt.cerkinfo.be/dists/unstable/contrib/source/Sources.gz) Could not resolve 'apt.cerkinfo.be'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

My sources list looks normal to me:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib

So can anyone help me fix this? I'm clueless.

---

### Post by namdung on 2008-12-21
Try removing or commenting the last 2 lines in the sources list


#deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
#deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib

---

### Post by jtskinner on 2008-12-21
Thanks for the reply but I tried what you suggested but it didn't have an effect I'm still getting the same problems.

---

### Post by unutbu on 2008-12-21
In your web browser go to [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
You'll see that the directory "feisty" is missing.

The file apt-get is looking for resides some place like here:

```
http://archive.ubuntu.com/ubuntu/dists/**feisty**/main/binary-i386/Packages.gz
```

But it does not exist. Note for gutsy the equivalent file does exist:

```
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz

```
I think the solution is to go to System>Software Sources and select a different server.

---

### Post by jtskinner on 2008-12-22
Yes that worked, that was the problem! Thanks for the help.

---

