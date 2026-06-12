---
title: "System slowdown"
date: 2008-08-24
forum: General Help
---

### Post by Cattus on 2008-08-24
Hi all,
I have a serious problem with Ubuntu 8.04 Hardy Heron. When I run programs or games using Wine or Dosbox, no matter how old, the system sooner or later suddenly freezes almost completely. Killing the process won't help: the system monitor tells that CPU usage remains almost 100%, although there isn't any processes running. Even restarting the computer doesn't solve the problem, instead I have to shut down the computer and wait for a while before turning it on again. This problem is quite new and I don't have any idea which could cause it. Any help would be greatly appreciated, thanks!

BTW, my computer is Acer Aspire with Celeron M370.

Finally, various test results:

#top:

top - 00:26:59 up 1:18, 3 users, load average: 2.80, 1.88, 1.25
Tasks: 107 total, 3 running, 103 sleeping, 0 stopped, 1 zombie
Cpu(s): 72.9%us, 20.4%sy, 0.0%ni, 0.0%id, 0.0%wa, 6.1%hi, 0.6%si, 0.0%st
Mem: 1026156k total, 953676k used, 72480k free, 24084k buffers
Swap: 2546292k total, 0k used, 2546292k free, 602364k cached

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
5206 root 20 0 358m 30m 9612 R 41.8 3.0 2:04.00 Xorg
5921 pystykoi 20 0 295m 97m 28m R 31.0 9.7 4:55.78 firefox
6056 pystykoi 20 0 99640 18m 11m S 13.1 1.8 0:09.28 gnome-terminal
5730 pystykoi 20 0 49996 30m 6456 S 8.4 3.1 0:52.54 wish8.5
6106 pystykoi 20 0 2308 1112 856 R 2.4 0.1 0:12.48 top
5710 pystykoi 20 0 15520 3044 2152 S 1.2 0.3 0:07.40 gnome-screensav
5745 pystykoi 20 0 83272 11m 8968 S 1.2 1.1 0:03.78 nm-applet
2435 root 15 -5 0 0 0 S 0.6 0.0 0:00.30 kjournald
5072 root 20 0 3420 1140 988 S 0.6 0.1 0:01.92 hald-addon-stor
1 root 20 0 2844 1692 544 S 0.0 0.2 0:01.34 init
2 root 15 -5 0 0 0 S 0.0 0.0 0:00.00 kthreadd
3 root RT -5 0 0 0 S 0.0 0.0 0:00.00 migration/0
4 root 15 -5 0 0 0 S 0.0 0.0 0:00.04 ksoftirqd/0
5 root RT -5 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
6 root 15 -5 0 0 0 S 0.0 0.0 0:00.06 events/0
7 root 15 -5 0 0 0 S 0.0 0.0 0:00.00 khelper
41 root 15 -5 0 0 0 S 0.0 0.0 0:00.18 kblockd/0

#ps:

PID TTY TIME CMD
6059 pts/0 00:00:00 bash
6642 pts/0 00:00:00 ps

---

### Post by linux_tech on 2008-08-24
Looks like xorg and firefox are using alot of resources
which makes me think it is likely a video or browser issue.
Are you also using compiz? 
What video card are you using?

---

### Post by Cattus on 2008-08-24
No, compiz and all desktop effects are disabled. Xorg and firefox take up all resources only after using wine/dosbox, but shutting down firefox doesn't change anything. My video card is intel 915G, integrated and slow enough.

---

### Post by Cattus on 2008-09-07
Now I've noticed the same problem with zsnes and even firefox..anybody got ideas? Now this problem's really annoying.

---

### Post by quoick on 2008-09-15
I've got exactly the same problem. I installed Linux Mint on a similarly specced machine to see if it was an Xorg/Firefox issue on the local machine and the Mint setup uses a fraction of the resources. I also installed the KDE and XFCE desktops on top of the Gnome one to see if that made any difference but alas no.

---

