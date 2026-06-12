---
title: "Can't boot into Ubuntu after failed XP installation"
date: 2008-09-15
forum: General Help
---

### Post by danwallace on 2008-09-15
I originally had Ubuntu installed. I tried to install XP on a second hard drive and the installation failed. Now when I try to boot it just says "no boot filename received" and restarts repeatedly.

I'm in the live cd right now and Gparted doesn't even detect any devices.

Any suggestions other than reinstalling everything??

---

### Post by danwallace on 2008-09-15
In fact, it won't even let me reinstall. It gets to the partition setup step and there's just nothing there.

---

### Post by danwallace on 2008-09-15
Anyone? My computer is basically useless right now.

---

### Post by caljohnsmith on 2008-09-15
OK, how about posting:
```
sudo fdisk -lu
```
That will give us some place to start.

---

