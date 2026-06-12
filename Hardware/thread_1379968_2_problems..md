---
title: "2 problems."
date: 2010-01-13
forum: Hardware
---

### Post by mercy16 on 2010-01-13
I come here asking help :(
I hope to offer it, some day.

I'm not a newbie to Linux, but I wouldn't say I'm advanced, either.

I have an Advent laptop, with Ubuntu Studio 9.1 on.
The more pressing issue, is getting my wireless to work. I've followed 3-4 walk-throughs, found one here, and the others on google. None of them have worked.

The other, less pressing issue, is that I used to run 3 screens in Windows. The laptop's screen, an external from the VGA port, and a third from a USB/VGA adaptor. Followed a walk-through for this, which involved creating a xorg.conf, and a bit at the bottom (System something...) that caused it to fail booting.

I tried the live disc, but could't fix it - lack of experience, I guess. In the end, I just re-installed the OS.

Is there any way to get the thing working? No real worries if not - it'd just be nice.


I have a basic knowledge of terminal... Opening, moving, copying, deleting and un/installing - but it's not extensive.


Thanks for any help that may come :)

---

### Post by mercy16 on 2010-01-14
Please?

---

### Post by lorsen on 2010-01-14
It is hard to help if one does not know which walk-throughs you tried and what error(s) you receieved.

Wireless:
Did you have a look at these pages:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Monitors:
Which tutorial did you use for this?

---

### Post by nothingspecial on 2010-01-14
1. You need to post your wireless card

```
sudo lshw -C network
```

---

