---
title: "download OS on different HDD"
date: 2018-05-16
forum: Hardware
---

### Post by idkwhatimdoing1.0 on 2018-05-16
Hi, I was wondering if it was possible to install Linux on a separate hard drive. I bought a connector thing and when I load my current OS on the computer I can see the hard drive no problem. And when I go to boot Ubuntu on the USB key it says where it would like me to install it on it can't find my hard drive... Yet everything is on. Does anybody know what I can do to make it work?

---

### Post by Bashing-om on 2018-05-16
idkwhatimdoing1.0 - hello -

Show us what it is that you are working with.
From the Ubuntu liveUSB post back - Between Code Tags - the output of terminal command:
```

sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
as the place to start to understand why you are experiencing difficulties installing ubuntu onto that external drive.


[INDENT][INDENT]all in the porcess[/INDENT][/INDENT]

---

### Post by idkwhatimdoing1.0 on 2018-05-16
hey problem solved. All I had to do was format the hardware (root) to be able to install OS on it.

---

### Post by Bashing-om on 2018-05-16
idkwhatimdoing1.0 :)

Good deal

[INDENT][INDENT]up up and away[/INDENT][/INDENT]

---

