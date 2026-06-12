---
title: "See CPU temperature from Linux?"
date: 2015-05-02
forum: Hardware
---

### Post by windofkeltia on 2015-05-02
I'm running an i7 on an ASUS z87 mobo. I'm looking for a way to observe or monitor the temperature of the CPU without shutting down then booting to the BIOS. This is a new box; I don't anticipate trouble, but I'd like to keep an eye on it if there's a way to do that.

Many thanks.

---

### Post by sandyd on 2015-05-03
Use the `sensors` command to view temperature of your CPU.

You may have to install lm-sensors if it is not included by default.

For more sensors, you can run
```

sudo sensors-detect
```
which will guide you through a process to detect more available sensors.

For GUI usage, there are a couple that you can use - conky, and some other widgets that may be specific to your Desktop Environment.

---

### Post by windofkeltia on 2015-05-03
Yup, that works fine. Profuse thanks, my friend!!!

---

### Post by warren3 on 2015-05-03
Psensor is also good from the software centre.

---

### Post by mattharris4 on 2015-05-04
^  That is what I use in both Edubuntu and Lubuntu (on different computers).  Unfortunately I can't tell if it is 100% accurate but it seems to be in the ballpark which is good enough for me since one computer runs in the upper 30's C and the other between 45 and 52 C.  A computer can usually handle heat well into the 70's C before causing problems, some can handle heat as high as 90 C.  Depending on how high you are compared to sea level the boiling point for water is about 100 C.

---

