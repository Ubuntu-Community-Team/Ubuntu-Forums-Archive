---
title: "Repository problem on Ubuntu 7.04"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by yeremiya on 2009-02-02
Hello, I have a big problem and I wonder if there is a simple solution for it, without having to install newer version of Ubuntu.

When I first installed Ubuntu 7.04 this morning, I had almost 300 updates to do. I let the updater download and install everything, and now when I want to install anything, I get these messages:

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


And in a box below, there's this:

```
http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.40 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.40 80]

```

I think it's **/etc/apt/sources.list** problem, but I have no idea how to change it so the installations and further updates could be executed.

Please, help!

---

### Post by Partyboi2 on 2009-02-02
Feisty has reached its end of life, you would be better off upgrading to a later release of Ubuntu. You are probably getting the error messages because the feisty repositories have been removed.

---

### Post by yeremiya on 2009-02-02
I was afraid that is the case. Is there any way to upgrade without reinstalling the whole system? Some kind of online upgrade? And is Ubuntu 7.10 supported? I've downloaded Ubuntu 8.10 iso but I can not install it, and also - can not run Live.

---

### Post by Partyboi2 on 2009-02-02
You could try [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/EOLUpgrades") guide. You can not skip releases so you will need to upgrade to gusty then on to hardy. 
Gusty is reaching its end of life soon as well, so best to upgrade to hardy or intrepid.

---

### Post by yeremiya on 2009-02-02
I've followed the instructions and this is what happens:

> root@leka-desktop:/tmp# sudo do-release-upgradeChecking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmpnGSy7s/gutsy.tar.gz'
authenticate '/tmp/tmpnGSy7s/gutsy.tar.gz' against '/tmp/tmpnGSy7s/gutsy.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main/debian-installer Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Done downloading            
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main/debian-installer Packages
Done downloading            
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Done [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main/debian-installer Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
100% [Working]  0s 


And it just hangs there... What should I do?

Edit:

After a while, this happened:
> Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]


(Btw, this thread is practically solved, I will mark it as soon as I succeed in updating my release... ;) )

---

### Post by yeremiya on 2009-02-02
I reply to my own message:

I've seen the errors I have made, and changed all feisty entries with gutsy... I hope this solves the problem...

---

### Post by yeremiya on 2009-02-02
It failed:

> Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]


The thing I don't understand is that I have no feisty entries in my sources.list anymore... Why does it tries to fetch feisty binaries!? Am I doing something wrong?

---

### Post by yeremiya on 2009-02-02
**Running partial update...**

---

