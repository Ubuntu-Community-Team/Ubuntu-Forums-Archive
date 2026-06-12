---
title: "stopping nethack from wanting to update"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by serria on 2009-05-01
I installed my own verison of nethack using the debuild, then dkpg is there anyway of stopping the update manager from wanting to install the default verison instead?

xubuntu 9.04, with all current updates.

---

### Post by loell on 2009-05-01
depending on how you named the package and if the software version is higher, the software won't be updated from package manager.

---

### Post by serria on 2009-05-01
ok, thanks i'll just increment the version so instead of 3.4.3-10 i'll have 4.4.3-10,  that should take care of the update.

Thanks for you help

---

### Post by anjilslaire on 2009-05-01
Also, you can direct apt to lock the version to prevent it from ever updating.
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[http://ubuntuforums.org/showthread.php?t=386884](http://ubuntuforums.org/showthread.php?t=386884)

---

