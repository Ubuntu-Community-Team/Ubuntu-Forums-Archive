---
title: "vanishing root device :-{"
date: 2010-11-08
forum: Hardware
---

### Post by engine on 2010-11-08
Aspire 1690, chugging along quite happily month after month ... until, the day after yet another unremarkable everything-working day, sudden refusal to boot.

start up portable from HD - select 9.10 kernel 2.6.31.22 from grub
starting up ...
ubuntu logo ...
black screen ...
ctrl + alt shows
```
Gave up waiting for root device. Common problems:3c150cd53d8
Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/[number] does not exist. Dropping to a shell.

BusyBox v1.13.3

{initramfs}

```

Booting from 9.10 live CD and checking the file-browser lists two XP partitions, then PQSERVICE and Filesystem - no sign of existing Linux partitions :-{

Might the "rescue existing system" option from the live CD be any help? and if so, how?

Thanks in advance for any tips and advice.

---

