---
title: "a recent update killed my suspend, need help finding which"
date: 2010-08-30
forum: Hardware
---

### Post by v1nsai on 2010-08-30
Suspend has happily worked for a while now, but yesterday it stopped working.  I checked the history in Synaptic and turns out I installed whatever updates were pushed 8-28-10, so one of those probably killed it.  

I started picking through the list but decided it would be easier to just reformat (I have /home on another partition) so I would only be running software from the official repos.  This didn't work, out of the box (after updating) I still can't suspend, so I'm guessing that something from the official universe repo is preventing it.

Can someone give me a list of what was updated so I can start rolling back?  I don't have a history list anymore since I formatted so can someone tell me what was updated in the last few days?  You can check this by going into Synaptic > File > History.

EDIT:
I forgot I copied the package list to my desktop so I could clean it up a little with *cut*.  I'm gonna copy it over here, can anyone see something that would interfere with suspend and/or power manager?

Thanks :-D

```
Commit


Upgraded
avant-window-navigator-data-trunk
avant-window-navigator-trunk
awn-applets-c-core-trunk
awn-applets-c-extras-trunk
awn-applets-common-trunk
awn-applets-python-core-trunk
awn-applets-python-extras-trunk
awn-settings-trunk
binutils
ghostscript
ghostscript-cups
ghostscript-x
libawn1-trunk
libgs8
libkpathsea5
libpackagekit-glib2-12
libpackagekit-qt-12
libservlet2.5-java
libvala0
packagekit
packagekit-backend-apt
python-awn-extras-trunk
python-awn-trunk
python-packagekit
texlive-binaries
tzdata
tzdata-java
ubufox
vala-awn-trunk
valac

Installed
libvala-0.10-0
valac-0.10

```

---

