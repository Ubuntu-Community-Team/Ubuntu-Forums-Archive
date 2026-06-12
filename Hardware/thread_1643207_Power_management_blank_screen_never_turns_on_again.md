---
title: "Power management: blank screen never turns on again.  nVidia 3100"
date: 2010-12-11
forum: Hardware
---

### Post by vangop on 2010-12-11
Hi!
I have HP 8440p and ubuntu 10.10 x64.
The problem is that I have "blank screen" option in the PM settings after 5 mins. This thing works weird: the screen first goes black (but still is on) and after that it just turns off (as expected).
But it doesn't turn on again when I drag mouse or press the keyboard buttons.
I've found the only solution - to switch thru virtual terminals ctrl alt Fx, making sure I click F7 and F8. Then it turns on and shows pass prompt.
I tried just ctrl+alt+F7 and F8 ones, but it takes more presses, so I go thru several others.
This is extremely annoying, can anybody suggest something?
I don't see anything unusual in logs, just 2x/min spam like
```
NVRM: os_raise_smp_barrier(), invalid context!
```
in syslog, but it is a nonstop spam. (which is my next on the fix list)

---

### Post by vangop on 2010-12-13
seems to be a driver issue, has reports on NV.
[http://www.nvnews.net/vbulletin/showthread.php?p=2363201]("http://www.nvnews.net/vbulletin/showthread.php?p=2363201")

---

