---
title: "Missing /lib/modules/`uname -r`/volatile/nvidia.ko on every reboot"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by jolger on 2007-11-08
Hi there i seem to have run in to somewhat of a misconfiguration of my own or a big bug XD

Trouble is ->
Each time i restart, my nvidia.ko file has mysteriously vanished, as soon as i reinstall the linux-restricted-module-`uname -r` everything works frine...

UNTILL i reboot :)

Now, has anyone experienced this before?

Running Ubuntu - Gutsy on a zepto znote 2425W...

1GB RAM (unknown manufacturer)
Mobo - unknown
GeForce go 7600
80GB Hdd.
CPU: Intel Core^1 Duo 1.8GhZ

just the few last lines of dmesg, since the laptop is currently not on the network...

Dmesg | tail

```

[   183.448933] nvidia: module license 'NVIDIA' taints kernel.
[   183.706178] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   183.706198] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   183.706850] NVRM: loading NVIDIA UNIX x68 Kernel Module 100.14.19 Wed Sep 12 13:12:24 PDT 2007

```

the stuff before that is just loading bluetooth stuff wich should have nothing to do with my problem...
on a reboot, startx gives me (Just rough details):

```

FATAL: Could not open '/lib/modules/2.6.22-14-386/volatile/nvidia.ko
(EE): Failed to load the NVIDIA kernel module!

```

doing a:
```

sudo updatedb
locate nvidia.ko

```

returns nothing, so i guess the system somehow deletes the file on shutdown or startup...

```

lspci | grep nV
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)

```

/Jolger AkA TP

---

### Post by jolger on 2007-11-09
Bumpzorz, need help please :)

---

### Post by jolger on 2007-11-10
This seems to happen only when running Gutsy, running Feisty atm, and everything works fine

/Jolger AkA TP

---

### Post by deGz0rx on 2007-11-19
this is what i get when i start my feisty fawn 7.04:
"...Using config file: "/etc/x11/xorg.conf"
FATAL Could not open
/lib/modules/2.6.20-16-generic/volatile/NVIDIA.ko: No such file or directory
Failed to load the NVIDIA kernel module
ABORTING
Screens found, but none have a usable configuration.

help me guys, i`m a poor guy with low level of IQ :lolflag:
xD
appreciated, deG

btw i`m not using lappy and i didnt wanna make a new topic sorry :D

---

### Post by Earendil1982 on 2008-07-12
Hey guys, try this:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/192931](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/192931)

At least it helped me.
Regards, Earendil1982

---

