---
title: "Xorg.conf?"
date: 2012-09-30
forum: Hardware
---

### Post by Rukiri on 2012-09-30
It's been awhile since I've used ubuntu but switched mainly because Adobe Master Suite CS6 runs flawlessly under wine(ran it under a VM under Funtoo and is my main reason for switch to Ubuntu as Cs6 will not install under Gentoo or Funtoo but works under Ubuntu)

Now usually the xorg.conf is under /etc/X11/xorg.conf, however I don't see it anywhere..  Does ubuntu have it located somewhere else?  Main reason as I have a Cyborg MMO7 mouse and I need to modify the xorg.conf for it to function properly otherwise I can't right click at all...

---

### Post by mikewhatever on 2012-09-30
Ubuntu has stoped using xorg.conf since about the 8.10 release. In case you need it, create the file. You can also auto-generate it with the 'Xorg -configure' command.

---

