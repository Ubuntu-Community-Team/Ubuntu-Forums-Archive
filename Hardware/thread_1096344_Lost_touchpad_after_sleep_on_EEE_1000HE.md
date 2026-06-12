---
title: "Lost touchpad after sleep on EEE 1000HE"
date: 2009-03-14
forum: Hardware
---

### Post by ygingras on 2009-03-14
I'm running 8.10 with a custom built 2.6.28.7 kernel on a EEE 1000 HE laptop.  Booth wifi and sleep work but when I come back from sleep mode the touchpad is not recognized.  If I logout, the touchpad is OK again at the GDM or the KDM screen.  If I switch user after sleep, the new session has a working touchpad but the orignial one, vt-7, is still stuck without touchpad.  The problem occurs with both KDE and Gnome.

Any idea on how I could hot-probe for the touchpad without logging out?  Being forced to do so king of beat the purpose of sleep mode.

---

### Post by ygingras on 2009-03-15
Resolved.  I installed the 2.6.27-11 kernel from [http://www.array.org/ubuntu/index.html](http://www.array.org/ubuntu/index.html)

Everything work now.

---

