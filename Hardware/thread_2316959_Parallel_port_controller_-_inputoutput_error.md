---
title: "Parallel port controller - input/output error"
date: 2016-03-12
forum: Hardware
---

### Post by bastpos on 2016-03-12
Hi. I'm sorry for my weak english language

I have a problem with the Parallel port. I use the operating system Ubuntu 14.04 (64 bit)
> $ uname -a
Linux x 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parallel port controller is not integrated with the motherboard. But is on the card plugged into a PCI slot
> $ lspci -v
0e:02.0 Parallel controller: MosChip Semiconductor Technology Ltd. PCI 9865 Multi-I/O Controller (prog-if 03 [IEEE1284])
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at be00 (size=8)
    I/O ports at bd00 (size=8)
    Memory at fbcfe000 (32-bit, non-prefetchable) 
    Memory at fbcfd000 (32-bit, non-prefetchable) 
    Capabilities: <access denied>
    Kernel driver in use: parport_pc

0e:02.2 Parallel controller: MosChip Semiconductor Technology Ltd. PCI 9865 Multi-I/O Controller (prog-if 03 [IEEE1284])
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at bc00 (size=8)
    I/O ports at bb00 (size=8)
    Memory at fbcfc000 (32-bit, non-prefetchable) 
    Memory at fbcfb000 (32-bit, non-prefetchable) 
    Capabilities: <access denied>
    Kernel driver in use: parport_pc

> $ cat /dev/lp0
cat: /dev/lp0: input/output error

$ cat /dev/lp1
cat: /dev/lp1: input/output error

> $ dmesg | grep lp
[    0.000000] On node 0 totalpages: 3143484
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5741.00 BogoMIPS (lpj=11482004)
[   20.166921] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   20.302553] lp0: using parport0 (interrupt-driven).
[   20.302597] lp1: using parport1 (interrupt-driven).


> $ cat /etc/modules
parport_pc
parport
lp
rtc
vhba

> $ groups ${USER}
p0su : p0su adm lp dialout cdrom sudo audio dip plugdev lpadmin sambashare

Parallel port controller not included software CD for Linux, so I dont installed anything special there. Please help me solve this problem

---

### Post by coldraven on 2016-03-13
Is this any help?

> In the end, removing libsane-hpaio did the trick, releasing the parallel port:
[http://ubuntuforums.org/showthread.php?t=2317056](http://ubuntuforums.org/showthread.php?t=2317056)

---

### Post by bastpos on 2016-03-13
> **coldraven said:**
> Is this any help?


[http://ubuntuforums.org/showthread.php?t=2317056](http://ubuntuforums.org/showthread.php?t=2317056)

Yes, now my printer is working :) Thanks for help.

---

