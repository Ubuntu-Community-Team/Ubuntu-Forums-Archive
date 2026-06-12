---
title: "Hardy Repository Issues - Dell Mini"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Hula2Pahoa on 2008-12-24
Hi all! I have been doing good with Ubuntu. I have a dell Mini 9 And it is running 8.0.4( I think that is the version?). I just received the Mini in October. I get the repository issues when I do the check for updates, as well. My question is how do I remove these? If it is not the version I have installed, then I must not need them, right? Here is my list:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]I would appreciate any help and assistance on this! TIA!
Can you tell me where to find my version?

---

### Post by kostkon on 2008-12-24
Hmmm, strange indeed. 

Anyways, could you post the contents of your sources.list file by open a terminal and giving
```
gedit /etc/apt/sources.list
```
and post them here?

---

### Post by mikewhatever on 2008-12-24
It is possible that these repositories are temporarily ofline, and all you need to do is wait a day or two. If that's not an option, try another server.

---

### Post by Dragonfi on 2009-01-09
There are no binary-lpia packages in theese repos, so apt-get cannot find them there, I don't know where can you get those packages to lpia architecture thoug..

[http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/)
[http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/)
(Follow the links yourself, if you want to see it)

---

