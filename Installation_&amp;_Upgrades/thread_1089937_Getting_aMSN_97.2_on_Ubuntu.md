---
title: "Getting aMSN 97.2 on Ubuntu"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by PaulTR on 2009-03-07
Warning: Linux Newbie :D

I was using the aMSN that installs with sudo apt-get install amsn, and I couldn't get the webcam to work, so I googled around to find an answer and I figure I need to switch over to the 97.2 version, but I'm having a Hell of a time trying to figure out how to get to it. I tried downloading the version for Linux but have no idea how to install it, and I was reading around and things are saying to unpack and some other stuff and I haven't a clue what that means <.< Just wondering if someone can give me a step by step so I can get through this when I have this problem later on with other programs. Thanks.

---

### Post by Partyboi2 on 2009-03-07
What version of Ubuntu are you using?

---

### Post by PaulTR on 2009-03-07
8.04 hardy

---

### Post by Partyboi2 on 2009-03-07
You can upgrade to 97.2 by enabling your backports in Software Sources (System>Admin>Software Sources) and on the "Updates" tab tick the box for backports. Then close Software Sources and upgrade amsn by opening Synaptic (System>Admin>Synaptic Package Manager) and searching for amsn and right click on it and select mark for upgrade.  After the upgrade you can disable backports if you wish.

---

