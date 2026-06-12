---
title: "Need Help with laptop installing amd driver"
date: 2012-08-12
forum: Hardware
---

### Post by captainswag on 2012-08-12
I have clevo laptop with model P150EM that comes with intel core-i7 3610M and AMD 7970M GPU . MY problem is that AMD catalyst does not detect my GPU . I downloaded amd catalyst through additional driver page , it installs fine but it doesn't not run because it doesn't detect my gpu. I suspected that intel graphics are ones being and used by the system and its blocking my amd gpu from being detected. I tried many methods installing amd catalyst and run it but it always fail. I also tries using the hybrid switching graphics tutorial but it also failed :

[http://ubuntuforums.org/showthread.php?t=1930450/](http://ubuntuforums.org/showthread.php?t=1930450/)

Unfortunately , I don't have a BIOS option to turn off intel graphics and switch only to dedicated graphics . Please I am stuck . I tried everything but so far no solution . I would be appreciated if somebody help me find solution. Thanks

---

### Post by captainswag on 2012-08-12
bump anyone  offer to help :P

---

### Post by captainswag on 2012-08-13
bump !

---

### Post by captainswag on 2012-08-15
it seems nobody willing to help ?

---

### Post by captainswag on 2012-08-16
bump!

---

### Post by Penguissimo on 2012-08-19
I don't think it's that nobody is willing to help so much as that not many people have this laptop and card. These threads indicate that it might just be a bug with the newest CCC:

[http://ati.cchtml.com/show_bug.cgi?id=555](http://ati.cchtml.com/show_bug.cgi?id=555)
[http://phoronix.com/forums/showthread.php?72936-issues-with-my-laptop-having-AMD-7970M-GPU](http://phoronix.com/forums/showthread.php?72936-issues-with-my-laptop-having-AMD-7970M-GPU)

---

### Post by Yellow Pasque on 2012-08-19
You probably have a hybrid graphics setup (an integrated Intel GPU + a discrete AMD GPU), and that's tricky to get running right.

Post output of:
```
lspci
```

---

