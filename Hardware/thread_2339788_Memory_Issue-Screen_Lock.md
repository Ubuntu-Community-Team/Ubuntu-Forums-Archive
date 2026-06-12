---
title: "Memory Issue-Screen Lock"
date: 2016-10-12
forum: Hardware
---

### Post by aviator1 on 2016-10-12
Hello All:

First time post in the hardware area.

I have an AMD 8530 4.0Ghz, 8 core, with 16GB RAM. I have a 256GB SSD drive and no swap. I was told not to do a swap on the SSD

I just recently upgraded to 16.04, but this particular problem existed with my 14.04, also.

Here it is. 

When working in various programs, Libreoffice spreadsheets for example, my computer will freeze. The screen dims and the sheet looks to be a variety of gray scales. This happens a few times a week, and I am a regular user.

I open the system monitor, and see that one of the 8 cores is maxed out at 100%. Other cores are less than 10%. RAM is at very little usage (1 GB out of 16).

Sometimes that core will clear itself, and then another core will pick up the 100% load, and the screen stays dim.

Usually, the entire issue clears in less than a minute. I cannot remember any time that I have to shut own and start again, but I probably have somewhere long the line.

Any ideas or suggestions?

Thanks for any replies.

---

### Post by tdeith on 2016-10-12
A quick way to diagnose which process is pinning your CPU is to run *top *in a terminal while working away. It will monitor your processes and their CPU load. If your entire desktop is graying out and freezing, then best results would be to have *top *visible when you expect your computer might freeze.

Once you know which process is pinning your CPU, figuring out why is easier.

---

### Post by aviator1 on 2016-10-12
Thanks for the info. Will give it a try.

Regards

---

### Post by aviator1 on 2016-10-13
Locked up and went gray this morning while using a spreadsheet. I was able to start Terminal-Top when it first dimmed, however, I do not have a clue what any of this means....if anything.

Anybody have any ideas? Thanks for any response.

```
   dave@dave-desktop:~$ top
 
 
 top - 05:42:21 up  1:19,  1 user,  load average: 1.30, 0.49, 0.36
 Tasks: 268 total,   3 running, 265 sleeping,   0 stopped,   0 zombie
 %Cpu(s): 14.3 us,  0.4 sy,  0.0 ni, 85.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
 KiB Mem : 16332236 total, 12770708 free,  1713268 used,  1848260 buff/cache
 KiB Swap: 16674812 total, 16674812 free,        0 used. 14212388 avail Mem  
 
 
   PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND      
  4677 dave      20   0 1426944 266732 120956 R  99.7  1.6   1:34.38 soffice.bin  
  2046 dave      20   0  621896  59048  32408 S   5.3  0.4   4:12.04 my-weather+  
  1671 dave      20   0 1644720 333468  87648 S   3.3  2.0   2:02.92 compiz       
  1062 root      20   0  322540 128336  64808 S   2.3  0.8   3:18.91 Xorg         
  4570 dave      20   0 1147940 312220 111028 S   2.0  1.9   0:53.43 firefox      
  1527 dave      20   0  647272  49664  26664 S   1.7  0.3   0:31.79 unity-pane+  
  1902 dave      20   0  506700  24760  19948 S   1.7  0.2   1:03.19 indicator-+  
  1580 dave      20   0  395940  12692  11156 S   0.7  0.1   0:23.85 indicator-+  
     7 root      20   0       0      0      0 S   0.3  0.0   0:06.89 rcu_sched    
  1215 dave      20   0   44156   4656   2872 S   0.3  0.0   0:21.38 dbus-daemon  
  1286 dave      20   0  345640   7464   5520 S   0.3  0.0   0:01.90 ibus-daemon  
  1946 dave      20   0  163728  20728   8180 S   0.3  0.1   0:14.57 python       
  4471 root      20   0       0      0      0 S   0.3  0.0   0:00.51 kworker/4:1  
  4970 dave      20   0  657588  36452  29048 S   0.3  0.2   0:00.40 gnome-term+  
     1 root      20   0  120136   6372   4072 S   0.0  0.0   0:01.43 systemd      
     2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd     
     3 root      20   0       0      0      0 S   0.0  0.0   0:00.05 ksoftirqd/0
```

---

### Post by aviator1 on 2016-10-13
Did it again just now with the same spreadsheet.

Here is what Top looks like. Are there any similarities?

```
dave@dave-desktop:~$ top

top - 16:01:25 up  2:50,  1 user,  load average: 0.98, 0.67, 0.37
Tasks: 266 total,   2 running, 264 sleeping,   0 stopped,   0 zombie
%Cpu(s): 15.2 us,  0.5 sy,  0.0 ni, 84.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 16332236 total, 12639220 free,  1810432 used,  1882584 buff/cache
KiB Swap: 16674812 total, 16674812 free,        0 used. 14104096 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 5543 dave      20   0 1465464 229968 120008 R 100.0  1.4   0:26.79 soffice.bin 
 2021 dave      20   0  623072  58084  32520 S   5.3  0.4   9:12.25 my-weather+ 
 1626 dave      20   0 1788440 267048 113780 S   4.0  1.6   2:43.32 compiz      
 1008 root      20   0  466096 168240  90688 S   3.0  1.0   2:41.66 Xorg        
 1475 dave      20   0  637948  40000  26164 S   2.0  0.2   0:58.56 unity-pane+ 
 5198 dave      20   0 1732236 526460 140612 S   1.7  3.2   3:31.70 firefox     
 1838 dave      20   0  506764  24836  20124 S   1.3  0.2   2:14.18 indicator-+ 
   52 root      39  19       0      0      0 S   0.3  0.0   0:00.41 khugepaged  
  117 root      20   0       0      0      0 S   0.3  0.0   0:01.23 kworker/3:2 
 1192 dave      20   0   44136   4616   2856 S   0.3  0.0   0:43.33 dbus-daemon 
 1263 dave      20   0  345388   6952   5396 S   0.3  0.0   0:00.66 ibus-daemon 
 1281 dave      20   0  521568  57764  39288 S   0.3  0.4   0:00.44 ibus-ui-gt+ 
 1318 dave      20   0  188388   5560   5212 S   0.3  0.0   0:00.09 ibus-engin+ 
 1542 dave      20   0  395940  12612  11088 S   0.3  0.1   0:54.49 indicator-+ 
 1884 dave      20   0  163732  20832   8248 S   0.3  0.1   0:29.66 python      
 5074 dave      20   0 1158072 297476  88940 S   0.3  1.8   0:54.28 thunderbird 
 5635 dave      20   0  657536  38380  29032 S   0.3  0.2   0:00.22 gnome-term+ 
```

I will be away for about a week. If anyone can make some suggestions, I would appreciate it. Regards.

---

### Post by aviator1 on 2016-10-22
Have been away for 8 days. Anybody have any ideas or suggestions.

It seems to mostly lock up using the spreadsheet, but sometimes with the browser.

Thanks.

---

