---
title: "Sony Vaio VGN-TZ26MN U7500 Intel Core 2 , CPU problem"
date: 2011-03-23
forum: Hardware
---

### Post by Jeff_1881 on 2011-03-23
HI All ,,

I have installed ubuntu 10.10, unfortunate it recognise only 1 cpu

uname -a output   

Linux Jeff-VGN-T26MN 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

jeff@Jeff-VGN-T26MN:~$ grep core /proc/cpuinfo
core id        : 0
cpu cores    : 1

I have searched the net for solution, :( I could not solve it. I tried PAE header

Others have made it but I do not how,

that's my summary
[http://browse.geekbench.ca/geekbench2/view/385081](http://browse.geekbench.ca/geekbench2/view/385081)
**[SIZE=1]System Information[/SIZE]**

    [SIZE=1]Operating System[/SIZE] [SIZE=1]Ubuntu 10.10 2.6.35-28-generic i686[/SIZE]    [SIZE=1]Model[/SIZE] [SIZE=1]Linux PC (Intel Core 2 U7500)[/SIZE] [SIZE=1]Motherboard[/SIZE] [SIZE=1]Unknown Motherboard[/SIZE]    [SIZE=1]Processor[/SIZE] [SIZE=1]Intel Core 2 U7500[/SIZE]   [SIZE=1]Processor ID[/SIZE] [SIZE=1]GenuineIntel Family 6 Model 15 Stepping 2[/SIZE]    [SIZE=1]Processor Frequency[/SIZE] [SIZE=1]1.07 GHz[/SIZE] [SIZE=1]Processors[/SIZE] [SIZE=1]1[/SIZE]    **[SIZE=1]Cores[/SIZE]** **[SIZE=1]1[/SIZE]** **[SIZE=1]Threads[/SIZE]** **[SIZE=1]1[/SIZE]**    [SIZE=1]L1 Instruction Cache[/SIZE] [SIZE=1]0.00 B[/SIZE] [SIZE=1]L1 Data Cache[/SIZE] [SIZE=1]0.00 B[/SIZE]    [SIZE=1]L2 Cache[/SIZE] [SIZE=1]2.00 MB[/SIZE] [SIZE=1]L3 Cache[/SIZE] [SIZE=1]0.00 B[/SIZE]    [SIZE=1]Memory[/SIZE] [SIZE=1]1.96 GB N/A[/SIZE] [SIZE=1]FSB[/SIZE] [SIZE=1]0.00 Hz[/SIZE]    [SIZE=1]BIOS[/SIZE] [SIZE=1]N/A[/SIZE]

others who ubuntu recognised their two cpu's
[http://browse.geekbench.ca/geekbench2/view/370057](http://browse.geekbench.ca/geekbench2/view/370057)

**[SIZE=1]System Information[/SIZE]**

    [SIZE=1]Operating System[/SIZE] [SIZE=1]Ubuntu 10.10 2.6.35-27-generic i686[/SIZE]    [SIZE=1]Model[/SIZE] [SIZE=1]Linux PC (Intel Core 2 U7500)[/SIZE] [SIZE=1]Motherboard[/SIZE] [SIZE=1]Unknown Motherboard[/SIZE]    [SIZE=1]Processor[/SIZE] [SIZE=1]Intel Core 2 U7500[/SIZE]   [SIZE=1]Processor ID[/SIZE] [SIZE=1]GenuineIntel Family 6 Model 15 Stepping 2[/SIZE]    [SIZE=1]Processor Frequency[/SIZE] [SIZE=1]1.07 GHz[/SIZE] [SIZE=1]Processors[/SIZE] [SIZE=1]1[/SIZE]    **[SIZE=1]Cores[/SIZE]** **[SIZE=1]2[/SIZE]** **[SIZE=1]Threads[/SIZE]** **[SIZE=1]2[/SIZE]**    [SIZE=1]L1 Instruction Cache[/SIZE] [SIZE=1]0.00 B[/SIZE] [SIZE=1]L1 Data Cache[/SIZE] [SIZE=1]0.00 B[/SIZE]    [SIZE=1]L2 Cache[/SIZE] [SIZE=1]2.00 MB[/SIZE] [SIZE=1]L3 Cache[/SIZE] [SIZE=1]0.00 B[/SIZE]    [SIZE=1]Memory[/SIZE] [SIZE=1]1.96 GB N/A[/SIZE] [SIZE=1]FSB[/SIZE] [SIZE=1]0.00 Hz[/SIZE]    [SIZE=1]BIOS[/SIZE] [SIZE=1]N/A[/SIZE]

please Help!

---

### Post by trundlenut on 2011-03-23
Does windows recognise two cores?  Assuming you have or have had windows installed.

---

### Post by Jeff_1881 on 2011-04-08
Before I installed ubuntu and get rid of Vista it used to recognise it as two core. In addition, the specs. of this processors is 2 core

[http://ark.intel.com/Product.aspx?id=29763](http://ark.intel.com/Product.aspx?id=29763)

[SIZE=1]Status[/SIZE]
[SIZE=1]Launched[/SIZE][SIZE=1]Launch Date[/SIZE]
[SIZE=1]Q3'06[/SIZE][SIZE=1]Processor Number[/SIZE]
[SIZE=1]U7500[/SIZE][SIZE=1]# of Cores[/SIZE]
[SIZE=1]2[/SIZE][SIZE=1]# of Threads[/SIZE]
[SIZE=1]2[/SIZE][SIZE=1]Clock Speed[/SIZE]
[SIZE=1]1.06 GHz[/SIZE][SIZE=1]L2 Cache[/SIZE]
[SIZE=1]2 MB[/SIZE][SIZE=1]Bus/Core Ratio[/SIZE]
[SIZE=1]8[/SIZE][SIZE=1]FSB Speed[/SIZE]
[SIZE=1]533 MHz[/SIZE][SIZE=1]FSB Parity[/SIZE]
[SIZE=1]No[/SIZE][SIZE=1]Instruction Set[/SIZE]
[SIZE=1]64-bit[/SIZE]
I do not know if I made the right decision to get rid of Vista,, 

is there anyway that could force ubuntu to recognise or a tweak somewhere to tell ubuntu that it has two core instead of one

---

### Post by trundlenut on 2011-04-11
It may worth trying booting from a live cd and see what ```
cat proc/cpuinfo
``` spits out.  Just to rule out a problem with the current install.

---

