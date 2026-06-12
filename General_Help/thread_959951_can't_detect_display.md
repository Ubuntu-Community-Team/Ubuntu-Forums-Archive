---
title: "can't detect display"
date: 2008-10-26
forum: General Help
---

### Post by krishna1650 on 2008-10-26
ubuntu 8.04 can't detect my display. there is option as system->preference->screen resolution. when i click detect display, it shows notging. my monitors refresh rate was 60, but here it is 50,which i can't change.
 thanks for help.

---

### Post by _sAm_ on 2008-10-27
Try:
```
sudo dpkg-reconfigure xserver-xorg
```

Read more here; [http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/](http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/)

---

