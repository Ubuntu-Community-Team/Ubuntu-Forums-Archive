---
title: "Dell 700m - No Sound"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by SkiSulli on 2006-12-25
I installed Ubuntu 6.10 on my Dell 700m laptop.  It works great except for the sound.  I can not get sound to play out of the laptop speakers.  If I plug in headphones or speakers then it works, but it will not work from the built in speakers.  I have tried everything that I can find on the internet to get the sound working and nothing has worked.  I could really use some help.  Thanks.

---

### Post by NeoLithium on 2006-12-25
In a terminal window, type:
```
alsamixer
```
Turn up the volume on all the options in there, and make sure none are muted. Should get it working again, since you can hear the headphones.

---

### Post by SkiSulli on 2006-12-25
Tried that, nothing was muted when I opened alsamixer.  Tried muting and unmuting everything and turning all the volumes to 100 and nothing has worked.

---

