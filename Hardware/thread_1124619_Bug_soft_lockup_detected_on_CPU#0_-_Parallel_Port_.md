---
title: "Bug: soft lockup detected on CPU#0 - Parallel Port Printer"
date: 2009-04-13
forum: Hardware
---

### Post by akssoon on 2009-04-13
Bug: soft lockup detected on CPU#0 - Parallel Port Printer

I have an Ubuntu box currently running Jaunty with a parallel port printer (Epson Stylus Color 400) connected to it. Sometimes I get a complete lockup meaning "Ctrl Alt" + Bspace|Del|F1|F2 etc. are not working anymore. Even the "gentle Restart" (see [1]) with
```
Alt + Print + "R E I S U B"
```
doesn't work.
The last time it happened I somehow managed to get to the "Ctrl Alt"+F1 terminal and saw that the following line got printed over and over again.
```
"BUG: soft lockup - CPU#0 stuck for 11s!
[parallel port]"
```
At that time the printer was connected but switched off. I switched it on and the computer got responsive again immediately.
Has somebody got an idea what the problem might be or where I could start looking? I did some research but couldn't find any reports of similar problems.

[1]http://kember.net/articles/231/reisub-the-gentle-linux-restart

---

