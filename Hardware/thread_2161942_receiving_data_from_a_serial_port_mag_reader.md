---
title: "receiving data from a serial port mag reader"
date: 2013-07-12
forum: Hardware
---

### Post by mlabieniec on 2013-07-12
I am trying to read a RS232 Serial Port with a Mag Stripe reader in Ubuntu 12.04. I have a USB one working fine (ID-Tech). But I am trying to get a Neuron reader to work as well. I am unfamiliar Serial Port communication in general, researching around it seems the tools to use are:


    sudo cat /dev/ttyS0


The problem I'm having is which port is the device attached to, doing the above on ttyS0,1,2,3 does nothing and should dump out some output from the device. However I'm not sure if this needs to be run first:


    sudo inputattach -dump /dev/ttyS0
This just hangs at the cursor and I figured to try and keyboard type for the card reader, but same issue just hangs. The output from dmesg | grep ttyS shows ports enabled:


    [    1.906700] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
    [    1.927250] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
    [    1.947758] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
    [    1.968273] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
    [    1.990199] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
    [    2.010770] 00:05: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
    [    2.031335] 00:06: ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
    [    2.051952] 00:07: ttyS3 at I/O 0x2e8 (irq = 11) is a 16550A

I also tried minicom, which didn't seem to get me anywhere either.

---

### Post by mlabieniec on 2013-07-16
So turns out I was doing everything correctly and there is a problem with the device. If anyone has any other suggestions besides gtkterm/cutecomm and/or just simply sudo cat /dev/ttyS0 for successfully reading/testing serial ports, and info is greatly appreciated.

---

