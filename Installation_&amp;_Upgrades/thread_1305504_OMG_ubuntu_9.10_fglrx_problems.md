---
title: "OMG ubuntu 9.10 fglrx problems"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by donald7777 on 2009-10-29
Hello Everyone, today I stupidly upgraded my ubuntu 9.04 to 9.10. Upgrade worked fine till it booted to the login screen where the screen turns black.

The only way I get picture back is to remove the xorg.conf file in  /etc/X11/ folder but then i get bad performance.

I believe it has something to do with fglrx because i get an error about it.

Please help.

---

### Post by Dimarchi on 2009-10-30
Did you type

```
sudo aticonfig --initial
```or

```
sudo aticonfig --initial -f
```in terminal once you installed fglrx (before reboot)? You may need to one of those. Those can be done after reboot, as well, but I prefer to issue one of the two before reboot to avoid getting a black screen.

---

### Post by donald7777 on 2009-11-02
i have tried activating flgrx by installing the driver under hardware drivers it downloaded but will not activate.

---

### Post by donald7777 on 2009-11-02
also my atheros AR5001 (Rev 01) wireless card no longer works.

---

### Post by donald7777 on 2009-11-02
flgrx is now fixed had to manulay remove it from package manager and ran the ati uninstaller just in case rebooted and downloaded the ati driver installed it and it works. will look at wireless tomorrow.

---

