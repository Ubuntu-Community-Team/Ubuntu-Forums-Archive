---
title: "upgrade to 8.1 results in no mouse or keyboard"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by tater_3001 on 2009-05-12
I recently upgraded to 8.1 so i could upgrade from there to the new release. however after the restart my mouse or keyboard wont work. my keyboad will work enough to let me in to command mode, however i never learned how to use that. Also it only lets me switch sometimes. other times it is colorful screen of like yellows and reds and purples instead of command line. does anybody know what my problem is and offer assistance? any help is greatly appreciated. thanks  Turner

---

### Post by sherwoos on 2009-08-01
I have the same problem and I'm just as lost in the command line. Please help!

---

### Post by wojox on 2009-08-01
Try:

```
sudo dpkg --configure -a
```

Restart

---

