---
title: "Hard disk activity slows access to other disks."
date: 2008-09-30
forum: General Help
---

### Post by psych787 on 2008-09-30
Basically, whenever I heavily use a disk, access to all disks slows down, as if all disks were the same. This includes filesystem usage, access to hard disk device files, VM disk usage, etc. Here are my system specs:

OS: 32bit Debain Etch
Kernel: Custom 2.6.24. Parameters used are vga=795 elevator=anticipatory nohz=off.
Processor: 2.4Ghz Quad-Core (Q6600)
Motherboard: NVIDIA 780i
RAM: 2GB 1066Mhz Dual-Channel
Graphics Card: 1 NVIDIA 8800GT with latest (173.14.12) drivers.
Disks: 3 SATA for storage, backup, and expendable data; 1 IDE for operating systems
Extensive CPU and RAM tests have shown no errors.

Some people recommended disabling the tickless kernel feature and using various IO Schedulers. While the anticipatory scheduler has greatly improved responsiveness, heavy disk use still causes problems.

Any ideas would be appreciated.

---

### Post by LoneWolfJack on 2008-09-30
this is just guessing, but years back I read about cheap mainboards that were "faking" SATA by chanelling it through IDE (basically, just plugging a SATA connector on top of the IDE bus)... this could be a possible explanation for your problems.

---

### Post by psych787 on 2008-09-30
I believe that applies to RAID, which I don't use.

Actually, the problem does seem like excessive cached memory, as VM speed at running DBAN picks up after a reboot, and swap is being used mysteriously despite having PLENTY of ram.

Generally, my problems seem to be similar to these:
[http://feedblog.org/2007/09/29/using-o_direct-on-linux-and-innodb-to-fix-swap-insanity/](http://feedblog.org/2007/09/29/using-o_direct-on-linux-and-innodb-to-fix-swap-insanity/)

Now the question is, how do I actually disable the cache for normal programs on a non RHEL system (hdparm doesn't help)?

EDIT: Setting /proc/sys/vm/swappiness has gotten rid of the bad swap behavior. Unfortunately, the real problem (poor performance with simultaneous disk access) still remains.

EDIT: Lucky me! I stumbled across ionice. Its too early to be sure, but ionicing QEMU-KVM when its running DBAN seems to have made the PC more stable.

EDIT: Unfortunately ionice has not eliminated the problem. Performance has improved, but several freezups occurred, and some disk intensive applications like ktorrent occasionally crashed.

---

### Post by psych787 on 2008-10-11
*BUMP*
The problem is still not solved. While ionice can stop an unruly program from completely hosing the system now, disk access should not affect other disks.

---

### Post by lavinog on 2008-10-11
What is your cpu load when accessing the disks? The system monitor on the panel helps breakdown your cpu load and may show how many cycles are for IOWait.
What mode is your sata controller operating in? (AHCI or IDE emulation)
There might be a bios setting for it.

---

### Post by psych787 on 2008-10-15
Thanks for the reply!
CPU load is practically nonexistant (<5%). However, I haven't found a way to monitor IOWait cycles.

Also, my bios (780i) provides no IDE emulation mode. I'd guess its in AHCI mode though, given that compiling a kernel with better SATA support improved reliability. However, here is the hdparm info on one of the SATA disks:
```
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30515/255/63, sectors = 490234752, start = 0
```

---

