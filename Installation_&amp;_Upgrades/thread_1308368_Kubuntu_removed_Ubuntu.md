---
title: "Kubuntu removed Ubuntu"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by joplass on 2009-10-31
Well I am multi booting with Windows7, Ubuntu, and Kubuntu.  My upgrade to Ubuntu 9.10 did not go too well and grub2 found W7 and gave me the usual list.  I also added Kubuntu on another partition now menu list does not give me Ubuntu as an option.  It is either Windows 7 or Kubuntu.  Is there a way to add the Ubuntu installation in the list?  I wanted to try Kubuntu because of the good things I heard about KDE4.3 :(.

---

### Post by bulldog on 2009-10-31
Usual,if you have to type your password,there's an option at the bottom to choose if you want to startup Gnome or KDE.
If you have,as you stated,different partitions with KDE and Gnome,I would think you have to add it manually to grub.

Maybe ```
sudo update-grub
```will help,otherwise take a look here.

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

