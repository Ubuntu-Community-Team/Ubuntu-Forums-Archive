---
title: "update fanager fails"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by amcelroy on 2009-11-11
I have just upgraded from 9.04 to 9.10 on my asus 901.  All is fine except the update manager only worked once and now fails as follows

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.



when I try manually it hangs as follows

amcelroy@amcelroy-laptop:~$ sudo apt-get update
[sudo] password for amcelroy: 
0% [Connecting to 10.66.011 (10.66.0.9)] [Connecting to 10.66.011 (10.66.0.9)]


any suggestions.

---

### Post by earthpigg on 2009-11-11
looks like one of ubuntu's many servers are down.

let your computer find another one:

system -> admin -> software sources -> download from -> other -> find best server

:D

---

### Post by amcelroy on 2009-11-11
tried that, but no change, by the way, my internet connection (wireless) works OK for browsing

---

### Post by earthpigg on 2009-11-11
> **amcelroy said:**
> tried that, but no change, by the way, my internet connection (wireless) works OK for browsing

can you show us your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by amcelroy on 2009-11-12
Got it sorted thanks.  I normally connect by wireless but used my ehernet connection at one time and for some reason it was trying to use that config even when plugged into a different DSL router.  I deleted the Auto eth0 in network manager and everything now works

---

