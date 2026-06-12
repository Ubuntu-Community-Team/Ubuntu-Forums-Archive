---
title: "Failed to Fetch- Upgrade"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by sirdouglas on 2008-12-09
I just reinstalled my ubuntu ultimate 1.4 edition, and now I am trying to upgrade to Ubuntu 7.10.  I can NOT get it to work though.  This error continuously pops up:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

What can I do?  Thanks guys,

Doug

---

### Post by sirdouglas on 2008-12-09
By the way, "/etc/apt/sources.list" consists of the following:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/apt/sources.list" 10 lines, 606 characters

Is there something that should have to be changed there?

Thanks again,

Doug

---

### Post by jenkinbr on 2008-12-09
Feisty has reached end of life, and the packages are being pulled from the servers little by little.

Your best bet is to download an ISO of ubuntu 8.04 Hardy Heron (Long-Term Support) or Ubuntu 8.10 Intrepid Ibex (latest Stable).

---

### Post by sirdouglas on 2008-12-09
Sounds like I'll be downloading that then.  Is it possible for me to upgrade to 8.10 without deleting my all my programs and files that I have on my current Ubuntu version?  

Thanks,

Doug

---

### Post by hikaricore on 2008-12-09
From what I can tell they didn't remove the packages so much as move them to a different server.

I was able to install new packages on the server I have at the office using the following in my sources.list:

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 

However the I was unable to upgrade to Gutsy this way. >.<
Guess I shouldn't have let that server sit with an old version for so long.

---

