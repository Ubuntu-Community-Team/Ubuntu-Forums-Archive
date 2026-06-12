---
title: "UltraVNC Viewer with WinXP + Ubuntu 9.04"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by BrJohn on 2009-10-19
I have 2 computers: one with Windows XP and one with Ubuntu. 
 
I always used UltraVNC Viewer to connect my computer with Windows XP to Ubuntu. I could normally access the graphical environment of Ubuntu, using the mouse and keyboard with no problem. 
  
  Unfortunately, I had the bad idea to upgrade my Ubuntu to version 9.04. 
 
  Now, I can connect the UtraVNC, however, the mouse clicks do not work!  
 
  I tried the latest version of UltraVNC and the problem persists. 
 
  Does anyone have any idea what may have happened?

Thanks!

---

### Post by BrJohn on 2009-11-02
Hi, I solved my problem with this:

```
sudo apt-get remove compiz compiz-core compiz-fusion-plugins-* compiz-gnome
```

---

### Post by Kareeser on 2009-11-02
A well known but not fixed bug. Which is quite terrible, because it effectively ruined Jaunty for me.

You don't have to remove compiz, you can simply turn it off.

```
metacity --replace

and

compiz --replace
```

---

