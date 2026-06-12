---
title: "CPU working at 100%"
date: 2011-06-09
forum: Hardware
---

### Post by KHIT on 2011-06-09
Hi
I have recently installed Xubuntu 11.04(with the alternate install CD) and discovered my system was working real slow. Therefore I installed System Monitor(the gnome one, which comes with standar ubuntu) and discovered that my CPU was working at 100%, even if I have nothing open and the system is idle.
The funny thing is that I can run Ubuntu 10.04LTS from LiveCD and it works faster than the Xubuntu 11.04 installed on my harddrive. I have the same issue with Ubuntu 11.04.
My system specs:
Model: Fujitsu Siemens ESPRIMO EDITION P2500
CPU: Intel Celeron D 346 3.07GHz
IGP: SiS 661FX 64MB
HDD: Western Digital 80GB 5400rpm
RAM: 1GB DDR SDRAM

I have another PC running Ubuntu, and it doesn't have the problem. Although this machine is running Ubuntu 8.10.
Model: IBM NetVista
CPU: Intel Pentium 3 990MHz
IGP: Intel 845GM 16MB
RAM: 384MB SDRAM
HDD: Seagate 20GB 5400rpm

Does the problem on the first machine occur because it has an On-board graphics chip instead of a PCI graphics card?

Thanks in advance

---

### Post by garvinrick4 on 2011-06-09
Open a terminal and run: ctrl/alt/t
```
top
```See what is taking all the cpu %

---

### Post by OnlineBuddy on 2011-06-09
look into the processes tab in system monitor to see which process is taking the most time?

---

### Post by KHIT on 2011-06-09
I have tried writing
```
top
```
in terminal. After that, I can open google chrome and CPU runs at 40% for a short time and then it jumps from 2-50%.
If I open google.com, it goes up to 65.6% and falls from there.
As soon as I open youtube and starts playing a movie it goes up to 90% and stays there.
At this point the process Xorg uses 50% of CPU.
If I launch Source Dedicated Server for Linux the srcds_linux process uses only 8.6% CPU and and Xorg runs between 45% and 50%. chrome uses about 40%
Total CPU usage is 85-90%
It doesn't get higher. It lags like hell but it doesn't really never reach 100%.
I tried with System Monitor, which told me that System Monitor it self uses about 20-30% CPU just for running. That explains why I thought it wsa using 100%

I think there might be a compatibility issue with my PC and Ubuntu distributions.
Compared to Windows XP, the same activity results in about 50% CPU usage.
On my other PC(IBM NetVista) Those actions result in 70% CPU usage with System Monitor on, but in Windows this resulted in 100% CPU usage.
It looks like when the graphics chip needs to work, the CPU usage rises.
I tried only with terminal open(with top command) to move it fast around the screen, and got the CPU usage up to 80%

If someone could recommend a Ubuntu distro which will run without this issue I would really appreciate that.

---

### Post by garvinrick4 on 2011-06-10
> As soon as I open youtube and starts playing a movie it goes up to 90% and stays there.
When you run flash player by Adobe it eats up cpu usage, it is a glut.

---

