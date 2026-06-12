---
title: "Scroll wheel issues in 8.10"
date: 2008-12-09
forum: Hardware
---

### Post by deadwing on 2008-12-09
I am using a Microsoft Trackball Explorer, and I just upgraded from 8.04 to 8.10.  Since the upgrade, my scroll wheel now scrolls horizontally, instead of vertically.  xev shows that the scroll wheel is using buttons 6 and 7.

Years ago, I used to use an xmodmap command to remap the buttons, but now it gives me an error:

```
$ xmodmap -e "pointer = 1 6 7 4 5 2 3"
Warning: Only changing the first 7 of 32 buttons.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  116 (X_SetPointerMapping)
  Value in failed request:  0x2
  Serial number of failed request:  9
  Current serial number in output stream:  9

```

Any thoughts?

---

### Post by deadwing on 2008-12-09
Well, imagine that - my problem was that I didn't define enough buttons in xmodmap:

```
$ xmodmap -e "pointer = 1 6 7 4 5 2 3 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32"
$ 

```

Of course, now I've lost the rest of my mouse buttons, but I think I can get it working through trial and error.

---

