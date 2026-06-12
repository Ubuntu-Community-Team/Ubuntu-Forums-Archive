---
title: "ATI dual monitors of different sizes"
date: 2008-08-20
forum: General Help
---

### Post by yang on 2008-08-20
I'm using 64-bit Ubuntu 8.04 and have xorg-driver-fglrx, and dual monitor display is "working."  However, my monitors are of different sizes.  The problem is that my single big desktop is sized so that the height and 50% of the width fit the (first) larger screen, whereas the (second) smaller screen can only display a portion of the second half of the desktop.  Ideally, I'd like my desktop to not be oblivious to the fact that I have multiple displays of different sizes (e.g., Windows handles this situation gracefully).

I'll describe what I see in the ATI Catalyst Control Center (amdcccle of fglrx-control).  Under Display Manager > Display Modes, I see only the options:

[LIST]
[*]Single (useless, just disables the second monitor)
[*]Clone (also useless, just two copies of the first display)
[*]Big Desktop
[/LIST]

The Display Area slider has only a single possible value: 3840x1200.

The two monitors listed are:

[LIST]
[*]DELL 2407WFP (under the detailed Information page, its max res is 1920x1200)
[*]VG171b (max res 1280x1024)
[/LIST]

Thanks in advance for any help!

---

### Post by mmarshall on 2009-03-27
You need to run something like this:

```
aticonfig --add-pairmode=1920x1200+1280x1024
```

You should then have 3200x1200 as an option.

---

