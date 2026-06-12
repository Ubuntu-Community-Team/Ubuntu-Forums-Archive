---
title: "ATI  x1100 Mobile fglrx problem"
date: 2008-08-31
forum: Hardware
---

### Post by Kykc on 2008-08-31
I have an ASUS F5RL notebook (Core2Duo T5250, ATI X1100, SB600 AMD Chipset, native display resolution 1280x800) And I'm facing strange problem. After enabling fglrx (proprietary driver) and restart I've got blank screen. After disabling driver in xorg.conf I'm able to boot back, but no luck with fglrx.. May be someone can help me? 
PS I'm using Ubuntu 8.04.1.

---

### Post by Kykc on 2008-08-31
Hm. I've fix it myself. If someone will have similar issue, may try:
1) delete xorg-fglrx and all compiz packages with synaptic.
2) Reboot
3) Install xorg-fglrx-envy package.
4) Reboot
5) Now system starts normally and I have 3D acceleration!
6) Install compiz back. All works!

---

### Post by ginin on 2008-10-14
Your solution worked for me as well :) Can use fglrx now with Ubuntu 8.04 and Ati X1100 on my Acer 5100. The mplayer would not play video (-vo x11 option would not play at full screen) all fixed now thanks!

---

### Post by ginin on 2008-10-14
I want to add that after the compiz installation, I could not get the fancy effects working automatically (setting in Preferences > Appearance kept asking to install the propietary driver) the solution was to run

```
compiz --replace
```

---

