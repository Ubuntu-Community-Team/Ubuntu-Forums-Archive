---
title: "6-port RS232 serial PCI card - 2 ports stop working"
date: 2012-11-25
forum: Hardware
---

### Post by huntkey on 2012-11-25
Hi experts,
My old Ubuntu 11.10 crashed. I installed brand new 12.04. However my serial PCI card starts to give me problems. My card should give me 6 RS232 serial ports. However only 4 are working. I googled and I have found some commands to show the information on my serial ports. They were used to be ttyS[456789]

```
dzhao@Server:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.234707] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.434548] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.503406] 0000:08:00.0: ttyS4 at I/O 0xe080 (irq = 16) is a ST16650V2
[    1.568669] 0000:08:00.1: ttyS5 at I/O 0xe400 (irq = 17) is a ST16650V2
[    1.626564] 0000:08:00.2: ttyS6 at I/O 0xec00 (irq = 18) is a 16550A
[    1.691837] 0000:08:00.2: ttyS7 at I/O 0xe480 (irq = 18) is a 16550A
dzhao@Server:~$ setserial -g /dev/ttyS[456789]
/dev/ttyS4, UART: 16650V2, Port: 0xe080, IRQ: 16
/dev/ttyS5, UART: 16650V2, Port: 0xe400, IRQ: 17
/dev/ttyS6, UART: 16550A, Port: 0xec00, IRQ: 18
/dev/ttyS7, UART: 16550A, Port: 0xe480, IRQ: 18
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0
```

Apparently the last two are showing me "unknown" status.. What does that mean? How can I fix it?

Can anybody please help..
Thanks!!

---

### Post by huntkey on 2012-11-26
Still need help... Thanks!!

---

### Post by coldraven on 2012-11-26
The only thing that I can think of is to take out the card and re-seat it.
It is possible that  plugging things into the card has made it move in it's slot.
Switch off the computer first!

---

### Post by huntkey on 2012-11-26
I never touched the hardware though... All I did was reinstalling the Ubuntu OS. However I will give it a try tonight! Thank you very much Coldraven

---

### Post by ummelum on 2012-12-09
is this solved?

if not, please take a look at the following:
[https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)
[http://ubuntuforums.org/showthread.php?t=2087953](http://ubuntuforums.org/showthread.php?t=2087953)
[http://ubuntuforums.org/showthread.php?p=12386601](http://ubuntuforums.org/showthread.php?p=12386601)
[http://ubuntuforums.org/showthread.php?p=12391994](http://ubuntuforums.org/showthread.php?p=12391994)
[http://ubuntuforums.org/showthread.php?t=2089911](http://ubuntuforums.org/showthread.php?t=2089911)

---

