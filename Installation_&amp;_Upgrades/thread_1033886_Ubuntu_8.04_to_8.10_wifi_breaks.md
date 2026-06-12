---
title: "Ubuntu 8.04 to 8.10 wifi breaks"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by Lord C on 2009-01-07
I bought a GIGABYTE WI07HT when I first got my Eee 901 and had a little trouble getting it working in Ubuntu 8.04. It worked fine in BT3 and other OSs.

[I found that if I added acpi=off]("http://ubuntuforums.org/showthread.php?t=920876&highlight=WI07HT") to Grub, the wireless worked fine. Of course this meant I had no battery monitor etc. but I could live with that.

After upgrading to Ubuntu 8.10 I thought that everything was working fine, then I realise the wireless network card is nonexistant. Ubuntu isn't recognising the wifi card at all. I've tried restoring Grub, to no effect. The wired network is fine.

Anyone have any ideas why the card would stop working on upgrade, and how to get it working again?

And yes, it is enabled in BIOS :)
[B]
[Update][/B]
Thanks to [this post](http://blog.security4all.be/2008/12/portablepwnage-part-4-installing-ubuntu.html) I've found a solution.

Install linux-backports-modules-intrepid-generic (for ath5k driver), comment out the blacklist in madwifi (/etc/modprobe.d/madwifi) and restart.

Lovely...

---

### Post by kurotenshi on 2009-01-07
I had a similar problem wich I solved using ndiswrapper, now it's all cool

---

