---
title: "Critical temperature reached 127C Auto Shutdown"
date: 2010-02-16
forum: Hardware
---

### Post by l1nuxfreak on 2010-02-16
Feb 16 17:04:28 debian kernel: [  523.563244] Critical temperature reached (127 C), shutting down.

Hi I've been having problems with my installation. I first used Ubuntu Server 8.04.4 then reformatted to Debian 5 to double-check. Same auto-shutdown problem on both so I do not think this is distribution specific.

I've searched for other people having the same errors but most were problems with Thinkpad T60 Notebooks.

Here are my specs:
ECS 671T-M Motherboard
Intel(R) Core(TM)2 CPU 4400 @ 2.00GHz
2GB Kingston DDR2 667 Memory
Seagate 160GB SATA
RTL-8169 Gigabit Ethernet
Linux debian 2.6.26-2-686 #1 SMP Wed Feb 10 08:59:21 UTC 2010 i686 GNU/Linux

Already scanned memory no problems. Also changed OEM HSF to a Thermaltake HSF. Still no joy.
---------------
So far here are my temps
IDLE = 47C

stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 10s
59-64C

stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 20s
63-68C

stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 30s
65-75C then jumped to 127C SHUTDOWN

---

### Post by l1nuxfreak on 2010-02-18
bump ... did I mention temp jumped from 70-127 in 2secs? It totally skipped 80-126C.

I don't think it would jump 40++C in 2-3secs

---

