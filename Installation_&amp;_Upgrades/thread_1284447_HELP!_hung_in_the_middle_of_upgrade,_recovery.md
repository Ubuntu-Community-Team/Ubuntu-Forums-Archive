---
title: "HELP! hung in the middle of upgrade, recovery?"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2009-10-06
Hello,

I had Ubuntu 8 something with two users - me and my girlfriend. Last night I started the upgrade process (to 9.04) on the administrator's side (user Me)
my girlfriend was working away this afternoon on her side and when I stepped in and flipped out of her user account over to mine to check the progress of the upgrade, when I flipped back to her side, the system seemed to hang.

after waiting a few minutes, I forced a power off.
on restarting, it comes to a blank coloured screen with a pointer arrow (which moves).
what have I done and how to I undo it? 
I can imagine powering down in the middle of an upgrade was not wise, but I didn't know how else to proceed.

Peter

---

### Post by Partyboi2 on 2009-10-07
Hi, are you able to boot into recovery mode? 
If you can boot into recovery mode try
```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by pjstock on 2009-10-07
thanks
how do I boot into recovery mode? does an option present itself (it doesn't currently) or do I have to hit F8 or something similar as in WIndows?

Peter

---

### Post by Partyboi2 on 2009-10-08
[[COLOR=Blue]This[/COLOR]]("https://wiki.ubuntu.com/RecoveryMode") will explain how to boot into recovery mode.

---

