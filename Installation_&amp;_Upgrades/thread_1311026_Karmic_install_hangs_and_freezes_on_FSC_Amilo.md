---
title: "Karmic install hangs and freezes on FSC Amilo"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by fbusse on 2009-11-02
On my old-fashioned laptop (FSC Amilo M 6300, 166 MHz Celeron, 1 GB RAM, 86C380 ProSavageDDR K4M266) Karmic hangs and freezes with black screen after requested reboot during fresh install (no update!) from alternate-CD.

The system did well on Hardy, where installation of Jaunty already revealed [the (presumably) same error]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/336311/comments/7").

Any ideas where to dig?
[URL="http://forum.ubuntuusers.de/topic/karmic-haengt-nach-installation/"]
(same question in German ubuntuusers forum)[/URL]

---

### Post by kwakosaure on 2009-11-02
Hello,
no solution, but I subscribe to your post : I get the same problem on an old laptop (VIA graphics too)

---

### Post by fbusse on 2009-11-03
canonical support suggests to try following instructions to install from landscape "[#2238 - Install a basic system and upgrade to a full installation](https://landscape.canonical.com/kb/article/2238)".

On my system, the result is the same as above. In the meantime, I got advice to collect further info and send to canonical. - I will keep you up-to-date.

---

### Post by fbusse on 2009-11-11
After removing from the boot options "quiet splash" and adding "debug=" (for further maintenance), at least the system got up to the GUI. After a first glance, it appears to be fully functional.

---

### Post by fbusse on 2009-11-13
Update: Only adding "debug=" does the job for me, too.

---

### Post by fbusse on 2010-05-03
this problem appears to be solved with Lucid for my system - great work, thanx to the team!

fresh install from the Kubuntu 10.04 desktop CD did it, only the bootsplash image [appears to be displayed with 8 colors]("http://launchpadlibrarian.net/47451791/Kubuntu_plymouth_splash_8_cols.png") - similar to the [known bug "Kubuntu Boot Splash Screen - Image Corrupted"]("https://bugs.launchpad.net/plymouth/+bug/571567").

starting (not installing) Kubuntu from the same CD got me a "hanging" system again.

---

