---
title: "mouse/keyboard freeze at same time. Computer still responsive. Asus Motherboard."
date: 2010-08-02
forum: Hardware
---

### Post by Zookalicious on 2010-08-02
Hi I just finished my first build and set up Ubuntu on it.

I have a couple of problems, but by far the biggest one right now is that after about a minute or two of normal usage, my keyboard and mouse freeze simultaneously. I swear my computer makes a clicking sound as they shut off too. The computer remains responsive, and plugging in a USB mouse will allow me to use it, but I would rather find out why my normal keyboard and mouse ports are not working. 

I'm using an IBM keyboard, an Acer Mouse and an Asus P7P55d-e Pro motherboard to connect them. CPU is an Intel i5-650 Dual Core. 

Any help is greatly appreciated.

---

### Post by byStanderone on 2010-08-02
...had experienced this problem in the past, and corrected it by using either one (keyboard or mouse) as ps2, not both as usb's...i surmise it must be an irq allocation problem.

---

### Post by Zookalicious on 2010-08-02
So I can't have both as ps2 or both as USB? That's unfortunate... Thank you for your prompt reply, but what do you think are the chances of a workaround? And is this an issue with ubuntu, the Asus motherboard, or just the combination of the two?

---

### Post by byStanderone on 2010-08-04
...can only speculate at the moment, it might as well be a hardware issue...having a hard time, (money wise) to upgrade hardware than the software.

---

### Post by utilitytrack on 2010-08-04
to **Zookalicious**

Hello, I offer you make some test.

1) [FONT=Courier New]$[/FONT] [FONT=Courier New]uname -r[/FONT]
2) [FONT='Courier New']$ free -m[/FONT]
3) run (be sure that you have 1GB free on [FONT=Courier New]/tmp[/FONT] directory)
 [FONT=Courier New]# dd if=/dev/zero of=/tmp/bigfile bs=1M count=1000[/FONT] 
4) together run 
 [FONT=Courier New]# vmstat -SM 1[/FONT]

please give your outputs and impressions here

---

### Post by Zookalicious on 2010-08-04
@bystanderone
I appreciate your speculation either way as it is obviously informed.

@utilitytrack
Thanks for your interest, I'm away from my computer for the next few days, but I'll be sure to update you wit the results of those tests once I'm back (Saturday).

---

### Post by Zookalicious on 2010-08-08
> **utilitytrack said:**
> to **Zookalicious**

Hello, I offer you make some test.

1) [FONT=Courier New]$[/FONT] [FONT=Courier New]uname -r[/FONT]
2) [FONT=Courier New]$ free -m[/FONT]
3) run (be sure that you have 1GB free on [FONT=Courier New]/tmp[/FONT] directory)
 [FONT=Courier New]# dd if=/dev/zero of=/tmp/bigfile bs=1M count=1000[/FONT] 
4) together run 
 [FONT=Courier New]# vmstat -SM 1[/FONT]

please give your outputs and impressions here

1) ```
2.6.32-24-generic
```
2)```
              total       used       free     shared    buffers     cached
Mem:          3955       1159       2795          0         74        473
-/+ buffers/cache:        611       3343
Swap:        11585          0      11585
```
3) ```
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 6.12801 s, 171 MB/s
```
4)```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1      0   1768     75   1473    0    0    54   107  153  771  4  1 93  1
 0  0      0   1768     75   1473    0    0     0     4  460 1294  1  1 98  1
 0  0      0   1768     75   1473    0    0     0     0  329  888  1  0 99  0
 0  0      0   1768     75   1473    0    0     0     0  403  939  1  0 98  0
 0  0      0   1768     75   1473    0    0     0     0  307  686  1  0 99  0
 1  0      0   1768     75   1473    0    0     0     0  463 1597  1  1 98  0
 0  0      0   1768     75   1473    0    0     0     0  490 3665  2  3 95  0
 1  0      0   1768     75   1473    0    0     0     0  374 1129  1  1 99  0
 0  0      0   1768     75   1473    0    0     0    32  346  822  1  1 96  1
 0  0      0   1768     75   1473    0    0     0     0  456 2107  1  1 98  0
 0  0      0   1768     75   1473    0    0     0     0  433 2168  1  1 99  0
 0  0      0   1768     75   1473    0    0     0     0  445 1546  1  1 98  0
 0  0      0   1768     75   1473    0    0     0     0  437 1612  1  1 97  0
 0  0      0   1768     75   1473    0    0     0     0  350  899  1  0 99  0
 0  0      0   1768     75   1473    0    0     0     0  361 1041  1  0 99  0
 0  0      0   1768     75   1473    0    0     0     0  407 1092  1  0 99  0
 0  0      0   1768     75   1473    0    0     0     0  420 1951  0  0 99  0
 0  1      0   1764     75   1473    0    0     0 82952  431 1115  1  2 95  2
 0  1      0   1764     75   1473    0    0     0 80896  475  738  1  1 73 25
 0  1      0   1764     75   1473    0    0     0 81920  540 1389  1  2 74 24
 0  1      0   1764     75   1473    0    0     0 65536  576 1468  1  2 73 24
```


I don't think it is anything relating to memory usage, because the computer itself is still perfectly responsive.... Just it acts like the mouse and keyboard are suddenly unplugged. Taking them out, and then plugging them back in does not solve the problem.

---

### Post by utilitytrack on 2010-08-08
You don't understood me. [FONT="Courier New"]vmstat[/FONT] has need run with [FONT="Courier New"]dd[/FONT] simultaneously and watch for system state. On the other hand I also was not careful and not closely read your first post, sorry. Ok, if you use PS/2 port the cause of your problem might be poor contact, for example. If you use USB it may be some other hardware issues. Try replace keyboard and mouse on a known good. Also check your system logs ([FONT="Courier New"]/var/log/messages[/FONT]) to find something similar:

[FONT="Courier New"]Oct 30 20:02:28 localhost kernel: [4376537.849000] psmouse.c: bad data from KBC - timeout
Oct 31 17:41:39 localhost kernel: [4366640.383000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[/FONT]
and/or

[FONT="Courier New"]May 26 10:10:38 localhost kernel: [ 5644.636000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
May 26 10:10:38 localhost kernel: [ 5644.636000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.[/FONT]

---

### Post by Zookalicious on 2010-08-24
Thank you for your help Utility. I just ended up using a USB keyboard and mouse.

---

