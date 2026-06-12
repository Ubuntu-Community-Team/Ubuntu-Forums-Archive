---
title: "Suspend problems"
date: 2010-06-18
forum: Hardware
---

### Post by 5oviet on 2010-06-18
I'm running Xubuntu 10.04 on an older laptop (HP Pavilion ze5600) and I'm having issues getting suspend to work. I've looked around for fixes and found that many people have similar issues but I'm quite new to linux and would appreciate some help. 

The system goes into suspend fine but when I try to wake it up I get a black screen and the system freezes completely. At one point I got the screen to turn back on but the system stayed frozen. This was after I tried the suggestion in [THIS]("http://ubuntuforums.org/showpost.php?p=2088093&postcount=2") post but after playing around with it more I broke it again and can't seem to find the combination that got the screen to work.

---

### Post by 5oviet on 2010-06-20
I tried all the possible combinations for those settings and the closest to working is with:
```

SAVE_VBE_STATE = false
DOUBLE_CONSOLE_SWITCH=false
USE_DPMS=false

```

The screen turns on and the system is operational for a few seconds, then it freezes up and the caps lock light flashes. Any ideas?

---

### Post by Buck At HelpDesk on 2010-12-24
I have the same problem
is it because of my motherboard's suspend mode settings?

---

