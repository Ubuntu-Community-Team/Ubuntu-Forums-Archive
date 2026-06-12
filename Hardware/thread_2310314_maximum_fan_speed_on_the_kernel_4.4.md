---
title: "maximum fan speed on the kernel 4.4"
date: 2016-01-18
forum: Hardware
---

### Post by yaneyev on 2016-01-18
[COLOR=#000000]I build a new [/COLOR][COLOR=#417394]kernel[/COLOR][COLOR=#000000] [/COLOR][COLOR=#417394]4.4[/COLOR][COLOR=#000000] on ubuntu. The hardware part - Compaq 615.[/COLOR]
[COLOR=#000000]There is a problem: after the release of the standby CPU cooler gaining [/COLOR][COLOR=#417394]maximum[/COLOR][COLOR=#000000] [/COLOR][COLOR=#417394]speed[/COLOR][COLOR=#000000] and keeps them all the time. Only solves reboot. At the default [/COLOR][COLOR=#417394]kernel[/COLOR][COLOR=#000000] 3.16.0-38 such problems did not arise. Tell me, what changed parameter when configuring the [/COLOR][COLOR=#417394]kernel[/COLOR][COLOR=#000000] to avoid this problem?[/COLOR]
[COLOR=#000000]Thanks in advance to all connoisseurs.[/COLOR]

---

### Post by Doug S on 2016-01-18
Kernel 4.4 isn't really supported here yet.
Your question perhaps should be over on the development forum, under the Kernel 4.4 RC thread. ([Here]("http://ubuntuforums.org/showthread.php?t=2303120"))
You might need to bisect the kernel to isolate the issue (bisection typically takes a lot of time). Or just monitor bug reports and such to see if others also have your issue and report it.

---

