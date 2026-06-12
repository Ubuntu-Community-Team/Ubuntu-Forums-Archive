---
title: "upgrade of nautilus not happening"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by randiroo76073 on 2009-09-30
Running 9.04 Jaunty
I've had a nautilus upgrade in synaptic for a month now and can't get it to upgrade because wrong ver of dependancies is to be installed. Any ideas as to a fix? These are error msgs I get:

libnautilus-extension1:
  Depends: libglib2.0-0 (>=2.21.3) but 2.20.1-0ubuntu2 is to be installed
  Depends: libgtk2.0-0 (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed

nautilus:
  Depends: libexempi3 (>=2.1.0) but 2.0.2-2 is to be installed
  Depends: libgail-common (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed
  Depends: libgail18 (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed
  Depends: libglib2.0-0 (>=2.21.3) but 2.20.1-0ubuntu2 is to be installed
  Depends: libgnome-desktop-2-11 (>=1:2.27.3) but 1:2.26.1-0ubuntu2 is to be installed
  Depends: libgtk2.0-0 (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed
  Depends: libselinux1 (>=2.0.82) but 2.0.65-5build1 is to be installed
  Depends: nautilus-data (>=1:2.27) but 1:2.26.2-0ubuntu2 is to be installed

---

### Post by zvacet on 2009-10-01
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by randiroo76073 on 2009-10-01
Thanks for reply zvacet, tried that and it didn't update nautilus files, only updated other programs that had updates in the pipeline :(

---

### Post by randiroo76073 on 2009-10-04
Am I the only one with this problem??? I still have a nautilus update in the synaptic pipeline that won't update, what gives???

---

### Post by randiroo76073 on 2009-10-17
Ya, well I tried to update today and it killed nautilus. Is no one else having this prob ??? Tried to re-install nautilus and this is what I get:
```

nautilus:
  Depends: libexempi3 (>=2.1.0) but 2.0.2-2 is to be installed
  Depends: libgail-common (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed
  Depends: libgail18 (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed
  Depends: libglib2.0-0 (>=2.21.3) but 2.20.1-0ubuntu2.1 is to be installed
  Depends: libgnome-desktop-2-11 (>=1:2.27.3) but 1:2.26.1-0ubuntu2 is to be installed
  Depends: libgtk2.0-0 (>=2.17.5) but 2.16.1-0ubuntu2 is to be installed
  Depends: libselinux1 (>=2.0.82) but 2.0.65-5build1 is to be installed
```

Does anyone out there have any help, this is getting ridiculous having an update in the repositories that breaks things. Where are the Dev's ? Pickin their nose or what !

---

### Post by randiroo76073 on 2009-10-18
Never mind, I solved it with a re-install of 9.04. Thanks to zvacet for his reply even tho it didn't help :)

---

