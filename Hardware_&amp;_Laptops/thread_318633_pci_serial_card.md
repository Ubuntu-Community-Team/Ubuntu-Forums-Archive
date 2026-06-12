---
title: "pci serial card"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by arcainus on 2006-12-14
Hi there

recently i have replaced my faxserver with ubuntu server 6.06.1 dapper.

i have two pci serial cards. the one pics up fine, with both ttyS6 and ttyS7 working fine.

the other card seems to be having issues it seems.

in the logs i find this

user@shadowfax:~$ dmesg | grep ttyS
[42949378.890000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949378.900000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949378.900000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949378.900000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949378.900000] 0000:01:04.0: ttyS4 at I/O 0xbc00 (irq = 11) is a 16550A
[42949378.900000] 0000:01:04.0: ttyS5 at I/O 0xbc08 (irq = 11) is a 16550A
[42949392.720000] 0000:01:01.0: ttyS6 at I/O 0xa000 (irq = 10) is a 16550A
[42949392.720000] 0000:01:01.0: ttyS7 at I/O 0xa400 (irq = 10) is a 16550A
[42949397.040000] ttyS4: LSR safety check engaged!
[42949397.040000] ttyS4: LSR safety check engaged!
[42949397.050000] ttyS5: LSR safety check engaged!
[42949397.050000] ttyS5: LSR safety check engaged!
[42949419.970000] ttyS4: LSR safety check engaged!
[42949419.970000] ttyS5: LSR safety check engaged!
[42949449.430000] ttyS5: LSR safety check engaged!
[42949451.660000] ttyS4: LSR safety check engaged!
[42949486.740000] ttyS4: LSR safety check engaged!
[42949486.770000] ttyS4: LSR safety check engaged!
[42949486.800000] ttyS4: LSR safety check engaged!
[42949486.830000] ttyS4: LSR safety check engaged!
[42949486.850000] ttyS4: LSR safety check engaged!
[42949486.880000] ttyS4: LSR safety check engaged!

i have a modem on ttyS0 (working fine)
and ttyS6 and ttyS7 (working fine)

i'm assuming that ttyS4 and ttyS5 is the other serial card?

some more info:

user@shadowfax:~$ lspci | grep Serial
0000:01:01.0 Serial controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
0000:01:04.0 Serial controller: Timedia Technology Co Ltd PCI2S550 (Dual 16550 UART) (rev 01)

user@shadowfax:~$ echo blabla > /dev/ttyS4
-bash: /dev/ttyS4: No such device

any ideas on what's wrong?

thanks
Geoffrey

---

### Post by arcainus on 2007-01-30
*bump*

---

