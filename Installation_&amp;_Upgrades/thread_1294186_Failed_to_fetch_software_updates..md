---
title: "Failed to fetch software updates."
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by T3nn0s on 2009-10-18
I have Ubuntu 9.04 and when I try sudo apg-get update or if I try to use the update manager I get a problem.
I am running on a XPS M1530.

I usually get something along the lines of this: 

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/restricted Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/main Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/restricted Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/restricted Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/universe Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/universe Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/universe Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/multiverse Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04/multiverse Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/main Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/restricted Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/restricted Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/universe Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/universe Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) 9.04-security/multiverse Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/multiverse Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 9.04-updates/multiverse Sources
  404 Not Found
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/9.04-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/9.04-security/main/binary-i386/Packages)  404 Not Found

And alot more than that but i'm not going to post all of it for the sake of readabillity.
Thanks in advance.

---

### Post by bulldog on 2009-10-18
Maybe the server you use is down or your internet connection fails to work.
Try another server instead or check if your connection is up.

---

### Post by T3nn0s on 2009-10-18
i already tried switching servers and it still was failing to fetch updates.

---

### Post by bulldog on 2009-10-18
For what it's worth,here some lines from my sources.list.
```
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

They seem a little different from yours.

---

