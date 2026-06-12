---
title: "Error during update to 9.10"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by vladimirt on 2009-10-18
Hello,

I&#7743; trying to update from 9.04 to 9.10 and I get this message:

¨Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages)  404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/karmic/main/source/Sources](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/karmic/main/source/Sources)  404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages](http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages)  404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/main/source/Sources](http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/main/source/Sources)  404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages)  404 Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.¨

Can somebody help please?

Thank you!!!

---

### Post by bulldog on 2009-10-18
Is it possible that the repos that where not found,are not existing for Karmic?
Maybe you should disable them by putting a # in front of them.
It could be wise for the future to disable all "non standard" repositories before you try to upgrade a distribution.

But to come back at your problem,besides the not found repositories,the update could be fine,maybe you can try to restart to see if it's functional.

---

### Post by lidex on 2009-10-18
vladimirt:
Open up your "software sources" and on the "third-party software" tab uncheck everything except the two canonical entries at  the top. Reload. Retry.

---

### Post by Tyegah on 2009-11-08
^^I have exactly the same problem and i did what you said. But then its failed still. 

the error message was :

Checking package manager
Reading package lists: Donem karmic/partner Packages: 00  
Reading state information: Done
Reading state information: Done
Reading state information: Done

Invalid package information 

After your package information was updated the essential package 
'ubuntu-minimal' can not be found anymore. 
This indicates a serious error, please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


any suggestions? I'm a newbie to ubuntu by the way.  any help would be highly appreciated

---

### Post by lidex on 2009-11-08
ubuntu-minimal is in the main repository. Run this command in terminal and copy/paste file content in post:
```
gedit /etc/apt/sources.list
```

---

