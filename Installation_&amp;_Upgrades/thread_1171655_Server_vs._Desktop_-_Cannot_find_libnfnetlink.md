---
title: "Server vs. Desktop - Cannot find libnfnetlink?"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Watership on 2009-05-27
When we install libnfnetlink on our Linux box running Ubuntu Server 8.04.2, we try to follow up by installing libnetfilter_queue... but the installation fails on the following error 

checking for LIBNFNETLINK... configure: error: Cannot find libnfnetlink >= 0.0.41


We've been working this one for an hour with no success so far... there must be some linker that's absent in the Ubuntu Server edition. Funny thing, the installation is clean as a whistle on our normal boxes (running Ubuntu Desktop 8.04.2.

Any ideas?

---

### Post by Watership on 2009-05-27
Ah... nevermind, we figured it out. For some reason our server version didn't come preinstalled with pkg-config, so our .configure command couldn't find the tool needed to find the appropriate programs.

Thanks anyway!

---

### Post by j.bailey on 2010-11-17
Hey there,

had the same problem, but thanks to your tip with pkg-config ...
Took me nearly two hours after I finally asked google and found this :(

---

