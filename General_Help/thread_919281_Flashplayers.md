---
title: "Flashplayers????"
date: 2008-09-13
forum: General Help
---

### Post by Dan78 on 2008-09-13
I've just reinstalled ubuntu, and went straight to youtube.com and can't view quick movies because of no flash player, it says click here to download adobe flash player 9, ....i've clicked that and now it's asking me which version to d/l for linux........there's 3 files   .tar.gz for linux or .rpm for linux or Yum for linux...which one should i d/l or is there a better package or flashplayer that i can install. pls help???

---

### Post by Crafty Kisses on 2008-09-13
You can install Flash from the Terminal by doing the following:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by jimmy the saint on 2008-09-13
install ubuntu restricted extras, which will give you flashplayer and a few other goodies.

1) Open a terminal
2) Type "sudo apt-get install ubuntu-restricted-extras
3) enter password
4) Enjoy

---

### Post by kokkus on 2008-09-13
You have to uninstall all other flash plugins (like gnash) to let it work.
(Incase you have them installed already)

---

### Post by aysiu on 2008-09-13
Instead of listening to YouTube (and going to the Adobe website), listen to Firefox (and have it install the appropriate plugin).

More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

