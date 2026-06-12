---
title: "Laptop freezes - Hangup"
date: 2008-10-09
forum: General Help
---

### Post by dheide on 2008-10-09
Hi everybody,

My laptop keeps hanging in random intervalls but at least once per day. I've been using ubuntu for years now and something like that never happened. 

Any help very much appreciated!!!!! 

My latop is an thinkpad T60p with ubuntu 8.04, kernel 2.6.24-21 and kde 3.5.10. What I can exclude:
- kernel: I tried older kernels from 8.04 but it still hangs
- gfx: I tried the frglx driver from ati and the radeonhd 

The last entry in the kernel log is most of the time something like

[ 5132.396439] ABORTED IN=eth0 OUT= MAC=00:1a:6b:6d:51:fd:00:1b:21:08:e4:fc:08:00 SRC=80.69.32.16 DST=192.168.1.103 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=TCP SPT=110 DPT=4600 SEQ=292587357 ACK=2154789925 WINDOW=0 RES=0x00 RST URGP=0 

The last thing I changed to the system before the hungups occured was to install the package 'linux-backports-modules-hardy-generic' to get my wifi working. The only other unusual thing is that I run the script tp-fancontrol to control the system fan.

Any suggestions???
Any ideas where to look??

Thank you very much!

---

### Post by dheide on 2008-10-12
Hi, 

my computer froze 5 times today within two hours :( , so if anybody has at least a hint where to look (log files, apps, ...) would be a great help. I tried to stop all kinds of running programs, but I was not able to find anythink.

Please help!

Dominik

---

### Post by asusx on 2010-12-27
Sorry for bumping an old thread, BUT
I'm having the same problem. My linux machine freezes when i have a thinkpad fan control enabled. It happens with xubuntu, ubuntu, archlinux.... I think the problem is with the linux kernel.

I have no idea how to fix it, but if anyone has a fix please post it.
I'm running on IBM T23 laptop.

---

