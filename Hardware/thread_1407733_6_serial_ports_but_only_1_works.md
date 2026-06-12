---
title: "6 serial ports but only 1 works"
date: 2010-02-15
forum: Hardware
---

### Post by sfabel on 2010-02-15
Hi all,

I need some help figuring out what is going on with an Intel 82801-DB LPC controller which handles the Super I/O in my motherboard. I don't know  the exact type of my motherboard (can anyone help me figure that one out?), but I know that it offers 6 serial ports, one over a regular DB9 interface, and five using the LPC bus.

Under Windows, the 6 ports show up as COM{1-6}. I am controlling some motors which are hooked up on COM4, 5 and 6. This works under Windows.

Under Linux, I only get /dev/ttyS{0,1,2,3}. This apparently can be controlled using either a kernel compilation option, or a boot parameter, which I tried:

```
8250.nr_uarts=6
```

However, ports 0-2 are dead, under ttyS3 I can access one motor. I've also got /dev/ttyS{4,5} now, but the I/O ports are messed up.

[B]A quick look in the BIOS revealed that serial port 5 lives at I/O 0x4e8 and port 6 at 0x4f8. 
[/B]
Looking at dmesg:
```

[    1.015356] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.015479] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.015619] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    1.015729] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    1.016355] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.016584] 00:10: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.016763] 00:11: ttyS2 at I/O 0x3e8 (irq = 3) is a 16550A
[    1.016937] 00:12: ttyS3 at I/O 0x2e8 (irq = 4) is a 16550A
[    1.017113] 00:13: **ttyS4 at I/O 0x4f8** (irq = 5) is a 16550A 
[    1.017289] 00:14: **ttyS5 at I/O 0x4e8** (irq = 9) is a 16550A

```

So I made sure I did not oversee anything; but I did not. Every time I change this in the BIOS, it shows up in reverse in dmesg; I cannot use setserial to change it, either. I should mention that the IRQs are set correctly and I've tried changing them (with one eye on the Serial-HOWTO), and these changes get accepted.

Now the above only shows the first four as output from serial8250, and then lists them again, this time all 6 of them.

What can I do? Is there a way to move /dev/ttyS{0-2} to wherever my motor controllers are? Do I recompile the kernel with some option enabled or changed? To I have to rewire the LPC port? Is support for the Intel 82801 DB LPC broken?

I would appreciate any help on this.

Thanks,
Stephan

---

