---
title: "Need help to recover Ubuntu installation"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Ren_Gar on 2009-07-19
I had installed Ubuntu on my Dell XPS desktop computer in a dual boot config with "crap" Vista. It all worked great for a while but i still needed Vista for a few apps. When I tried to upgrade Vista to SP1, Vista would not boot up after the upgrade failed. I then decided to reinstall vista from scratch (after backing up my Hard drive) But now i can't boot into my Ubuntu Installation any more, (not on the same physical drive) I know it's all there but i can't get it... any ideas?

---

### Post by merlinus on 2009-07-19
Boot from the live cd, open a terminal and enter:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)
quit 
```

and restart.

---

