---
title: "GRUB 2 will be the default boot loader"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by philetus on 2009-10-31
When I upgrade, will GRUB 2 pick up my Windows partition or will I have to reinstall Windows?

---

### Post by QIII on 2009-10-31
If you upgrade, you won't get GRUB2.  You will be left in a "legacy mode".  If you do a fresh install, you will get GRUB2.

But you can install GRUB2 in Jaunty.

See my post (number 8 ) here:  [http://ubuntuforums.org/showthread.php?t=1299098](http://ubuntuforums.org/showthread.php?t=1299098)

Don't reinstall Windows.

Just make sure you don't overwrite it during the partitioning phase of the installation.

To get GRUB2 to pick it up as a dual boot option, boot back to Karmic and do

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```

---

### Post by philetus on 2009-10-31
Thank you QIII. I was worried. I'm getting tired of installing and reinstalling this week.

---

