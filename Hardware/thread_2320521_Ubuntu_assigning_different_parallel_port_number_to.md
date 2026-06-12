---
title: "Ubuntu assigning different parallel port number to same device"
date: 2016-04-14
forum: Hardware
---

### Post by go-diaz01 on 2016-04-14
I am currently running Ubuntu 15.10 64-bit on a laptop.
I bought a USB to Parallel Port adapter from StarTech model [B]ICUSB2321284.
[/B]Here's the product page link: [B]
[https://www.startech.com/Cards-Adapters/Serial-Cards-Adapters/1s1p-USB-Serial-Parallel-Adapter-Cable~ICUSB2321284](https://www.startech.com/Cards-Adapters/Serial-Cards-Adapters/1s1p-USB-Serial-Parallel-Adapter-Cable~ICUSB2321284)
[/B]
I could not install the official driver. Kept running into this:

```
gerardo@UX00:~/Downloads/Linux/Linux_7715_V1.8$ sudo makemake -C /lib/modules/4.2.0-35-generic/build -I /lib/modules/4.2.0-35-generic/build/drivers/usb/serial SUBDIRS= modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-35-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/bin2c
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf  --silentoldconfig Kconfig
make[2]: *** No rule to make target 'arch/x86/entry/syscalls/syscall_32.tbl', needed by 'arch/x86/entry/syscalls/../../include/generated/asm/syscalls_32.h'.  Stop.
arch/x86/Makefile:184: recipe for target 'archheaders' failed
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-35-generic'
Makefile:12: recipe for target 'default' failed
make: *** [default] Error 2

```

Regardless, on connecting the adapter, I was still able to use the parallel port.

**Pyparallel tries to access /dev/parport0 by default. And everything worked the first time around.**
[B]
Problem is, on disconnecting and connecting the adapter, python could not find /dev/parport0 anymore, however, the parallel port was still working.
I monitored what happened every time I disconnected and connected the adapter using [/B]

```
ls -al /dev/parpot*
```

[B]I found out that everytime that I disconnected and connected the adapter, Ubuntu assigned a different parport number to the device,
here's what happened after a couple of reconnections:[/B]

```

gerardo@UX00:~$ ls -al /dev/parport*
crw-rw-r-- 1 root lp 99, 5 abr 14 15:53 /dev/parport5
gerardo@UX00:~$ ls -al /dev/parport*
ls: cannot access /dev/parport*: No such file or directory (here the adapter was disconnected)
gerardo@UX00:~$ ls -al /dev/parport*
crw------- 1 root root 99, 6 abr 14 15:55 /dev/parport6
gerardo@UX00:~$ ls -al /dev/parport*
crw------- 1 root root 99, 7 abr 14 15:55 /dev/parport7
gerardo@UX00:~$ ls -al /dev/parport*
crw-rw-r-- 1 root lp 99, 7 abr 14 15:55 /dev/parport7
gerardo@UX00:~$ ls -al /dev/parport*
crw-rw-r-- 1 root lp 99, 8 abr 14 17:39 /dev/parport8

```

**Any idea on how to fix this so Ubuntu assigns the same parport number to the adapter every time?**

Note: On boot, Ubuntu does not allow access to parport. Every time the computer starts I need to run:
```
sudo rmmod lp
sudo modprobe ppdev
```

This allows me to access parport.

I am also aware of some people having problems using:

```

sudo modprobe parport
sudo modprobe parport_pc
```

I'm not sure if that helps.

Anyway, thanks for your time!

---

