---
title: "Firefox sources"
date: 2008-11-02
forum: General Help
---

### Post by vlc on 2008-11-02
Hi *,

I would like to have a look on the Firefox sources used by Ubuntu. So I activated "Source Code" in the "Software Sources" dialog and updated the packages, but I cannot see any Firefox-related source package in the package manager. There is firefox-3.0-dev, but it contains the development libraries and headers, but it says nothing about sources.

I also checked that the deb-src lines are included in "/etc/apt/sources.list":

```
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
```

Is there anything else I have to configure or does the Firefox source package have a name without "firefox" or "mozilla"?

Thanks a lot in advance!

---

