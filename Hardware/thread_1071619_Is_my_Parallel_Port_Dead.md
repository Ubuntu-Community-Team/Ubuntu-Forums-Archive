---
title: "Is my Parallel Port Dead?"
date: 2009-02-16
forum: Hardware
---

### Post by bandyo on 2009-02-16
I have an old desktop with a HP Laserjet 5P attached to the parallel port. Recently it stopped working. So I tried deleting the driver and re-installing. Now the computer is not finding the parallel port. dmesg shows:

$ dmesg | grep par
[    0.380023] Booting paravirtualized kernel on bare hardware
[    4.374334] PM: Resume from partition 8:5
[   14.090094] parport_pc 00:0a: reported by Plug and Play ACPI
[   14.090407] parport_pc 00:0a: disabled
[  181.123538] ppdev: user-space parallel port driver
[  184.327685] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or

The parallel port is enabled in the BIOS. How do I find out if it is the old computer's hardware or some software issue?

Thanks

---

### Post by cariboo on 2009-02-16
The only thing I can suggest is to make sure the parport driver is installed:

```
lsmod | grep par
```

should result in something like this:

```
lsmod | grep par
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
```

Jim

---

### Post by bandyo on 2009-02-17
Thanks Jim. My output of lsmod does not look like yours.

```
$ lsmod | grep par
parport_serial         14336  0 
parport_pc             39204  1 parport_serial
parport                42604  2 ppdev,parport_pc

```

What does it mean? How do I fix it?

Thanks again.

Bandyo

---

### Post by cariboo on 2009-02-18
Can you load the lp module manually?

In a terminal type:

```
sudo modprobe lp
```

It looks like for some reason the lp module doesn't load when the parport is loaded.

Jim

---

### Post by bandyo on 2009-02-18
Thanks Jim. Manual loading seems to work. After the modprobe, lsmod includes lp.

```
$ lsmod | grep par
parport_serial         14336  0 
parport_pc             39204  1 parport_serial
parport                42604  3 lp,ppdev,parport_pc

```

Bandyo

---

### Post by bandyo on 2009-02-19
I must have tried to modprobe too many times unloading lp last time. To be sure I rebooted the machine and tired the commands lsmod and dmesg again. lsmod shows lp is loaded. However, dmesg shows the parport_pc is disabled.

```

$ lsmod | grep par
parport_pc             39204  0 
parport                42604  3 ppdev,lp,parport_pc

$ dmesg | grep par
[    0.380023] Booting paravirtualized kernel on bare hardware
[    4.523215] PM: Resume from partition 8:5
[   13.893221] parport_pc 00:0a: reported by Plug and Play ACPI
[   13.893497] parport_pc 00:0a: disabled
[   24.564612] ppdev: user-space parallel port driver
[   27.710341] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or

```

It will be great if anyone has any ideas about what is going on. 

Thanks

Bandyo

---

