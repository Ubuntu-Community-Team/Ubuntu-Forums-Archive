---
title: "Will installing Gentoo hurt my Home partition?"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by kahlil88 on 2009-03-07
I have a separate Home partition and would like to install Gentoo. Will the install delete or overwrite anything?

---

### Post by tommcd on 2009-03-07
Good luck with Gentoo! I have never been brave enough to try it.
Are you installing Gentoo *in place of* Ubuntu? Or are you installing Gentoo onto a separate partition so you can dual boot both Ubuntu *and* Gentoo?

If you are replacing Ubuntu with Gentoo, then Gentoo should not delete your data in /home. I would remove all the hidden config files in /home before installing Gentoo just to avoid any conflicts.

If you are going to dual boot Ubuntu and Gentoo, then just choose a different user name in Gentoo so that all the hidden config files in /home don't conflict with each other. I use a separate /data partition for my data to avoid this since I boot more than one distro.

---

### Post by kahlil88 on 2009-03-07
I made a backup of the Ubuntu partition, so when I have Gentoo up and running I'll add it to the GRUB menu as something to fall back on until I'm ready to use Gentoo exclusively.

---

