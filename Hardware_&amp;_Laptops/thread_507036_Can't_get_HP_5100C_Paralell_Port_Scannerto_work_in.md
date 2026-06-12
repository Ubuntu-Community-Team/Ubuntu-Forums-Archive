---
title: "Can't get HP 5100C Paralell Port Scannerto work in Feisty."
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-07-22
From thread [http://ubuntuforums.org/showthread.php?t=455500](http://ubuntuforums.org/showthread.php?t=455500) I gathered that I needed to get the ppscsi and epst modules working, but when following the instructions, it all works except the EPST module which gives:

root@ifrit:~# sudo modprobe epst
FATAL: Error inserting epst (/lib/modules/2.6.20-16-generic/kernel/drivers/parport/epst.ko): No such device

I have tried changing EPP modes in the bios, but nothing seems to work. The scanner is powered and connected.

dmesg gives the following:

dmesbulldog@ifrit:~$ dmesg | grep par
[   52.918266] Booting paravirtualized kernel on bare hardware
[   31.616000] parport: PnPBIOS parport detected.
[   31.616000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   32.908000] lp0: using parport0 (interrupt-driven).
[   47.920000] ppdev: user-space parallel port driver
[  100.768000] ppdev0: registered pardevice
[  100.816000] ppdev0: unregistered pardevice
[ 1078.536000] ppdev0: registered pardevice
[ 1078.588000] ppdev0: unregistered pardevice

Anyone have an idea?

---

### Post by CheeseEatingBulldog on 2007-07-26
No one have an idea as to how to force my parallel port scanner to be detected?

---

### Post by geraldm on 2007-07-26
```

scanimage -L

```
Above command provides a list of devices.  Rarely detects parallel port scanners, which
are difficult to identify.

Perhaps driver hp5100c.zip from HP under wine ?

Gerald

---

### Post by CheeseEatingBulldog on 2007-07-27
No scanner is detected. And a windows driver will definitely not work. I can't get the EPST module to install, as the scanner isn't being seen on the parallel port. :(

---

