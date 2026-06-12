---
title: "Stuck installing parallel port card"
date: 2009-11-17
forum: Hardware
---

### Post by penjuin on 2009-11-17
Hi all,

I recently purchased a CH352 based single parallel port PCI card. lspci follows:
```
04:07.0 Serial controller: Device 4348:5053 (rev 10) (prog-if 02)
	Subsystem: Device 4348:5053
	Flags: medium devsel, IRQ 17
	I/O ports at cf00 [size=8]
	I/O ports at ce00 [size=8]
	Kernel driver in use: serial
```

There appears to be linux drivers on the disc I received with it, however I am having trouble getting them going on ubuntu. The instructions say to copy the "install_p_80x86" file to /usr/sbin and then add it to rc.local. To test it, I didn't bother with the rc.local part and just ran it in terminal. I received the following errors:

```
ERROR: Module lp does not exist in /proc/modules
ERROR: Module parport_pc does not exist in /proc/modules
insmod: can't read '/lib/modules/2.6.27-7-generic/kernel/drivers/parport/parport_pc.o': No such file or directory
insmod: can't read '/lib/modules/2.6.27-7-generic/kernel/drivers/char/lp.o': No such file or directory
```

So I did a modprobe lp and modprobe parport_pc and now I still have the last two errors:

```
insmod: can't read '/lib/modules/2.6.27-7-generic/kernel/drivers/parport/parport_pc.o': No such file or directory
insmod: can't read '/lib/modules/2.6.27-7-generic/kernel/drivers/char/lp.o': No such file or directory
```

Now I understand that the latest kernel uses .ko files because they can be linked by the kernel itself, but is there anywhere I can get the .o files? Or alternatively, can anyone see a simple solution to my problem (I am running kernel 2.6.31-14-generic on a vanilla 9.10 install)?

---

### Post by any_stuff on 2009-12-05
i`ve got the same issue, but on ubuntu 9.10 x64
simple instruction following didn`t bring up any result
can anyone give some advice?

---

