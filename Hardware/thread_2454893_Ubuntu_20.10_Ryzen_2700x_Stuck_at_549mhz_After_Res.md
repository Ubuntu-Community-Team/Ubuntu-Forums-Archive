---
title: "Ubuntu 20.10 Ryzen 2700x Stuck at 549mhz After Resume From Suspend"
date: 2020-12-08
forum: Hardware
---

### Post by lakerssuperman2 on 2020-12-08
[COLOR=#D7DADC][SIZE=3][COLOR=#000000][FONT=arial]Greetings.

[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=arial]I'm  currently running Ubuntu 20.10 on my system with a Ryzen 2700x CPU I  recently picked up.  The mobo is an Asus Hero VI.  Everything works  wonderfully, except for one issue.  When I suspend and then wake the  computer, the system is incredibly slow and laggy.  Barely usable.
[FONT=arial black][/FONT]
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=arial]After  some digging I found that the CPU is stuck at 549mhz after suspend (as  reported by cpufreq-info).  Rebooting the system brings the clocks back  to normal.  cpufreq-info rerprts in the 2.2ghz range after reboot which  is the correct lowest speed step reported.  The CPU governor is set to  performance both before and after the suspend/resume cycle.

[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=arial]I've looked around the web and found a variety of posts of similar issues, but nothing recent and specifically for Ubuntu (a lot of Windows stuff).

[/FONT][/COLOR][/SIZE]

[FONT=arial][SIZE=3][COLOR=#000000]Does anyone have a fix they could recommend?  Help is much appreciated.[/COLOR][/SIZE]
[/FONT]
[/COLOR]

---

