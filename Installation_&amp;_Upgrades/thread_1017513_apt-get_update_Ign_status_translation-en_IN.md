---
title: "apt-get update Ign status translation-en_IN"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by eskhool on 2008-12-21
I have Intrepid Ibex installed as an upgrade from Hardy. I've tried googling this with no luck. I get a lot of failures with apt-get update around TRANSLATION-EN_IN but I don't have that in my repositories. Is this normal? 

```
sudo apt-get update 
```

Get:1 file: apt-build Release [89B]
Ign file: apt-build/main Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_IN
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_IN
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_IN
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_IN
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main Translation-en_IN

---

### Post by Partyboi2 on 2008-12-21
From what I understand ign means it hasn't fetched it because you already have the
file with the same date. Its part of the normal operation of apt-get update

---

