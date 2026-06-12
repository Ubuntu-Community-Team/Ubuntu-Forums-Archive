---
title: "Using apt-p2p"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by mathfeel on 2009-10-30
I upgraded to Karmic using the alternative CD (Yesterday's server load was atrocious). Now I want to run dist-upgrade on my system. Meanwhile I decided to try out apt-p2p and see if it's faster in downloading package files, but apt-get update always freezes at:
```
$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027) karmic/restricted Translation-en_US
Get:1 http://localhost karmic Release.gpg [189B]
Ign http://localhost karmic/main Translation-en_US
Ign http://localhost karmic/restricted Translation-en_US
Ign http://localhost karmic/universe Translation-en_US
Ign http://localhost karmic/multiverse Translation-en_US
Get:2 http://localhost karmic-updates Release.gpg [189B]
Ign http://localhost karmic-updates/main Translation-en_US
Ign http://localhost karmic-updates/restricted Translation-en_US
Ign http://localhost karmic-updates/universe Translation-en_US
Ign http://localhost karmic-updates/multiverse Translation-en_US
Get:3 http://localhost karmic-security Release.gpg [189B]
Ign http://localhost karmic-security/main Translation-en_US
Ign http://localhost karmic-security/restricted Translation-en_US
Ign http://localhost karmic-security/universe Translation-en_US
Ign http://localhost karmic-security/multiverse Translation-en_US
Get:4 http://localhost karmic Release [65.9kB]
Get:5 http://localhost karmic-updates Release [44.1kB]
Get:6 http://localhost karmic-security Release [41.7kB]
Get:7 http://localhost karmic/main Packages [1,353kB]
Get:8 http://localhost karmic/restricted Packages [7,971B]
Get:9 http://localhost karmic/universe Packages
Get:10 http://localhost karmic/multiverse Packages [190kB]
Get:11 http://localhost karmic-updates/main Packages [3,920B]
Get:12 http://localhost karmic-updates/restricted Packages [14B]
Get:13 http://localhost karmic-updates/universe Packages [1,093B]
Get:14 http://localhost karmic-updates/multiverse Packages [14B]
Get:15 http://localhost karmic-security/main Packages [14B]
Get:16 http://localhost karmic-security/restricted Packages [14B]
Get:17 http://localhost karmic-security/universe Packages [14B]
Get:18 http://localhost karmic-security/multiverse Packages [14B]
99% [9 Packages bzip2 0]
```

Anyone knows if it's apt-p2p's problem or what?

--M

---

### Post by H4F on 2009-11-02
I think you shouldn't have space in:
Get:4 [http://localhost](http://localhost)    here       karmic Release [65.9kB]
More that that you have to specify localhost port which apt-p2p is listening on(default 9977)
Get:4 [http://localhost:9977/karmic](http://localhost:9977/karmic) Release [65.9kB]- this how it should look like

---

### Post by mathfeel on 2009-11-20
> **H4F said:**
> I think you shouldn't have space in:
Get:4 [http://localhost](http://localhost)    here       karmic Release [65.9kB]
More that that you have to specify localhost port which apt-p2p is listening on(default 9977)
Get:4 [http://localhost:9977/karmic](http://localhost:9977/karmic) Release [65.9kB]- this how it should look like

This is a line in source.list:
```

deb http://localhost:9977/us.archive.ubuntu.com/ubuntu/ karmic restricted main

```

And 9977 is open.

---

