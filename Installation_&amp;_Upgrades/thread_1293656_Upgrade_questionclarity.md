---
title: "Upgrade question/clarity"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Rifester on 2009-10-17
I recently updated from Jaunty to the beta version of Karmic.  I love the changes!   Great work and thank you to everybody that is working so hard on Ubuntu development.  You should be proud!   I did not perform a clean install as I had everything running perfect in Jaunty and set up just how I wanted it.   Am I correct in my understanding that by NOT performing a clean install I will not be running the most current version of GRUB or ext4?
If this is true, are there any future negatives about this?  Is performance effected by not doing a clean install?   Thanks for your help/advice as this was the first update of my system.

Mark

---

### Post by mac9416 on 2009-10-17
> Am I correct in my understanding that by NOT performing a clean install I will not be running the most current version of GRUB or ext4?

Yes, to the best of my knowledge, that's correct. However, you can upgrade GRUB by following [these instructions]("http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html").
I'm afraid you can't move to ext4 without reinstalling, though.

Hope that helps!

---

### Post by Rifester on 2009-10-17
Thanks for the instructions!

---

### Post by Rifester on 2009-10-17
I followed the GRUB update instructions perfectly.    I did a test boot from the chainload menu and everything booted up.   So I:
 $sudo upgrade-from-grub-legacy
Everything ran fine in terminal.    I rebooted the system and now I get grub error 15 and the system locks up.  I had to dig out my Jaunty live disk to get online.    PLEASE HELP!

---

### Post by mac9416 on 2009-10-17
Sorry about that, I hadn't tested that tutorial, and I hope it's OK.

Others have had this problem. Someone found [this fix]("http://kubuntuforums.net/forums/index.php?topic=3106892.0").

```
$ sudo update-grub2
```

Hopefully that fixes it.

---

### Post by QIII on 2009-10-17
> **mac9416 said:**
> Yes, to the best of my knowledge, that's correct. However, you can upgrade GRUB by following [these instructions]("http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html").
I'm afraid you can't move to ext4 without reinstalling, though.

Hope that helps!

Actually, you can change to ext4.

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

---

