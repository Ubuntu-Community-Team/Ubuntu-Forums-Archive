---
title: "installing software to offline machine"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by def boss on 2009-07-04
hey every body 
i use ubuntu hardy and my machine is offline , i go to a friend who has an internet connection and uses windows os to download packages but i always have problems with dependencies , is there any web site i can get the packages with all its dependencies One-time?

note : 
i tried to get software and dependencies from [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) , but it made me mad .

---

### Post by abhigyan91 on 2009-07-04
just research a little about what you are dloding and make sure to dlod the dependencies also.. lol

normally deb files have everything..

---

### Post by apparle on 2009-07-04
I think this is the best solution for you
[http://keryxproject.org/](http://keryxproject.org/)
If this is not useful then try this but it is a little complicated

[http://ubuntuforums.org/showthread.php?t=310020](http://ubuntuforums.org/showthread.php?t=310020)

---

### Post by sabby on 2009-07-04
Hello Def,

Please try the below link:
```
http://labs.fajran.web.id/p/apt-web/index.php
```

Just select the base distro, mirror and type in the package name which you wish to download.
This will list all the deb package you would need to install and download.

Once the all the packages are downloaded, just run the below from the directory where all the packages have been downloaded.
```
sudo dpkg --force-overwrite -i *.deb
```

---

### Post by abrari on 2009-08-22
Yeah, apt-web. I love it because i have kinda limited internet connectivity.
But it only provide packages from indonesian server (because it is indonesian-student-made).

---

### Post by mac9416 on 2009-08-23
+1 for [Keryx]("http://keryxproject.org/")

Although it's not web-based, it is very simple and will make your life offline much easier.

---

