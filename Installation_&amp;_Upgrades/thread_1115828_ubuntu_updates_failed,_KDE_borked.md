---
title: "ubuntu updates failed, KDE borked"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2009-04-04
I have (had) the KDE base libs etc installed so I could use such programs as ktorrent and krusader, but when I tried to run some updates this morning (from the ubuntu update notification) I got an error relating to package identification. Now I find myself with a broken KDE installation and I can't fix it. 

Kdelibs needs to be reinstalled but it won't install itself because...

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-runtime: Depends: libstreamanalyzer0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
                   Depends: libstreams0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
  kdelibs5: Depends: libstreamanalyzer0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
            Depends: libstreams0 (>= 0.6.3) but 0.5.11-1ubuntu2 is to be installed
E: Broken packages

```

What can I do?

edit: sorry, found a duplicate thread

---

### Post by redkimdk on 2009-04-12
Which tread is that duplicate tread?

Never mind I found it myself. I am guessing its this post.
[http://ubuntuforums.org/showthread.php?t=1114928](http://ubuntuforums.org/showthread.php?t=1114928)

---

