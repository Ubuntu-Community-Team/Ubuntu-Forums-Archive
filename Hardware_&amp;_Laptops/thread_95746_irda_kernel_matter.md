---
title: "irda: kernel matter"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by mirons on 2005-11-27
Hi everybody! My irda port is getting me mad because of something wrong in the kernel. It gets the device (I'm pretty sure it is /dev/ttyS1, port 0x02f8 with uart 16550a and irq3) and loads the proper modules (irtty_sir,sir_dev,irda, according to lsmod), but everytime I try to start the device with */etc/init.d/irda-setup start* this is what I get:

> [4295474.321000]     ACPI-0508: *** Error: Method execution failed [\_SB_.PCI0.SBRG.UAR2._SRS] (Node dffead40), AE_AML_BUFFER_LIMIT
[4295474.321000] pnp: Failed to activate device 00:06.

I also tried to activate it through /sys/bus/pnp/device/00:06/resources interface, but stil with no result (The configuration changes, while it shouldn't and the devices is still disabled; This is the command I used: *#echo "manual 01 dynamic" > /sys/bus/pnp/device/00:06/resources*). I really don't know what else to do. My computer is an asus A4700L, attached you find the complete output of dmesg. The same device works perfectly with knoppix 3.7, kernel 2.6.9.

Thanks for reading this message.

---

