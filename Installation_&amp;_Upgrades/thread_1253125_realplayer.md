---
title: "realplayer"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by mulligan on 2009-08-29
i have downloaded realplayer using the instructions from the following link.

[http://everydayubuntu.blogspot.com/2008/05/how-to-install-realplayer-in-ubuntu-804.html](http://everydayubuntu.blogspot.com/2008/05/how-to-install-realplayer-in-ubuntu-804.html)

it all went as planned whoever it does not show in the application sound and video section.

below is the last result from the terminal when installed.

Copying RealPlayer files...No write-permission to  /etc/profile.d ...skip.
Succeeded.
installing application icons resource...
installing document icons resource...
...Succeeded.
Configuring Mozilla...
Installing .mo locale files...
Setting selinux context...
/usr/share or /usr/bin no write-permission...skip.

RealPlayer installation is complete.
Cleaning up installation files...
Done.

morgan@morgan-desktop:~$

---

### Post by oldos2er on 2009-08-29
Try running **sudo ./RealPlayer11GOLD.bin**. This will give you the necessary permissions. When that's done, run Applications, Sound & Video, Realplayer 11.

---

### Post by mulligan on 2009-08-29
> **oldos2er said:**
> Try running **sudo ./RealPlayer11GOLD.bin**. This will give you the necessary permissions. When that's done, run Applications, Sound & Video, Realplayer 11.

yep that got it working thanks for the tip.

---

