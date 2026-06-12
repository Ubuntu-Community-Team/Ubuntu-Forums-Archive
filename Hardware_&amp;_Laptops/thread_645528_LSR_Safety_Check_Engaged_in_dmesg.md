---
title: "LSR Safety Check Engaged in dmesg"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by craftybones on 2007-12-20
Hello,

I am running Feisty on a computer with additional serial ports. By default the current kernels of linux only offer 4 runtime uarts. However, in spite of this, 2.6.20-16 was able to see the additional serial ports. However, recently, a problem seems to have developed and the following line pops up in dmesg:


[   44.955993] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   44.956451] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   44.956795] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   44.957156] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   44.961059] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   44.961667] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   44.962389] 00:0a: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
[   44.962969] 00:0b: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A
[   44.963547] 00:0c: ttyS4 at I/O 0x2f0 (irq = 11) is a 16550A
[   44.964119] 00:0d: ttyS5 at I/O 0x2e0 (irq = 10) is a 16550A
[   84.687428] ttyS4: LSR safety check engaged!
[   84.689418] ttyS4: LSR safety check engaged!
[   96.613069] ttyS4: LSR safety check engaged!

Now as you can see, ttyS4 doesn't seem addressable. Therefore, I decided that perhaps we needed to recompile the kernel to allow more than 4 runtime UARTS, and even after that the same thing persists.

I am not sure what the error is. I have the lspci info if anyone can help me with this.

Thank you,

Craftybones

---

