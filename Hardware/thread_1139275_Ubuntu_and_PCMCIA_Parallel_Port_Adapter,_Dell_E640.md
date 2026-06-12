---
title: "Ubuntu and PCMCIA Parallel Port Adapter, Dell E6400 Laptop"
date: 2009-04-26
forum: Hardware
---

### Post by dukbilt on 2009-04-26
Hello everyone,

I have been trying to use a PCMCIA parallel port adapter under Ubuntu 8.10 (64-bit) on a Dell E6400 Laptop but cannot use ECP mode.

When I install the PCMCIA adapter (a Trans Digital Corporation Trans PC Card Universal Parallel Port) and in a terminal window enter:

[INDENT]**dmesg | grep parport**[/INDENT]

I receive the response:

[INDENT][   14.543777] parport 0x378 (WARNING): CTR: wrote 0x0c, read 0xff
[   14.543784] parport 0x378 (WARNING): DATA: wrote 0xaa, read 0xff
[   14.543785] parport 0x378: You gave this address, but there is probably no parallel port there!
[   14.543809] parport0: PC-style at 0x378 [PCSPP,TRISTATE]
[   14.658989] lp0: using parport0 (polling).
[242627.834865] parport1: PC-style at 0x2378, irq 19 [PCSPP,TRISTATE]
[242627.834883] parport1: irq 19 in use, resorting to polled operation
[242627.931289] lp1: using parport1 (polling).
[/INDENT]

I have the BIOS set to use ECP mode, however I think this is more to do with the docking station parallel port (which I don't have).

I have tried the above command on a much older laptop, with a proper parallel port, running Ubuntu 8.10 (32-bit) and it identifies the parallel port as ECP mode.

Can anyone help me set up the parallel port so it uses ECP?

Thanks,

dukbilt

---

