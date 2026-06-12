---
title: "System tools like that of Sysinternals?"
date: 2008-11-20
forum: General Help
---

### Post by jasonkirk2006 on 2008-11-20
Hi;

I've been using Ubuntu for some time. I'm looking for system tools that will give detailed system information on Linux. There are very nice tools developed by Sysinternals (now part of Microsoft Technet) on Windows. Namely Process Explorer, Process Monitor, TCP Viewer etc. System monitor in Gnome desktop or the similar monitoring tools of the KDE environment is just insufficient compared to that of Sysinternals, by the help of which you can get plot of instant memory usage, I/O delta bytes, all the handles used by a specific process etc. And Process Monitor logs all the system activity taking place and even log the boot process right from the start to the end.

Does anybody know equivalent of Process Explorer, Process Monitor and similar tools from Sysinternals?

---

### Post by Nepherte on 2008-11-20
For processes, you can use the 'top' command:
```
top
```

---

### Post by tom66 on 2008-11-20
Taking a stab in the dark, but if you would like those programs, they *might* work under Wine. As far as I know, System Monitor also offers extra information: you can see User, Virtual Memory, Resident Memory, Writable Memory, Shared Memory and X Server Memory, but you have to enable them under Preferences.

---

### Post by jasonkirk2006 on 2008-11-20
> **Nepherte said:**
> For processes, you can use the 'top' command:
```
top
```

Not even compares. I want more detailed information like path of the process image, handle count, list of every individual handles, services that run under each process, memory usage, cpu usage (history), i/o history etc. Since i use a GDM, i want a visual tool.

---

### Post by sedawk on 2008-11-20
If you are happy with the command line I would recommend:

lsof (file handles, sockets, etc)
top (process monitoring like task manager)
netstat (network)
vmstat (memory usage)

More tools are part of the "sysstat" package which is not
installed by default, e.g.
iostat (disk i/o)

Then you can check "sar" which has a long history.

There might be front-ends for all of these (so you have output
like with "process monitor" from sysinternals).

---

### Post by olejorgen on 2008-11-20
/proc/<pid>/ contains lots of information. Not very nicly represented though.
```

iotop # disk io delta per thread/process
htop # improved top
xrestop # x stats
powertop # power usage stats
slabtop # some kernel stats

```

---

### Post by jasonkirk2006 on 2008-11-21
Thanks for replying.

---

