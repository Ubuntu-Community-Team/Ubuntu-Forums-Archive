---
title: "/dev/ttyS0 disappears, only solution complete reboot."
date: 2011-02-06
forum: Hardware
---

### Post by DishBreak on 2011-02-06
All,

I'm currently running Ubuntu 10.10 on a Dell Latitude D600, and I've got an issue with the serial port. Every so often, when I fire up minicom, I get no output on the terminal. 

I've noticed two potential clues. When the serial port stops working, I see the following:
```
vishal@XXXX:~$ dmesg | grep ttyS0
[    0.629082] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.630224] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[13345.195255] ttyS0: LSR safety check engaged!

```
My searching so far shows that this means the system can no longer access the serial port via /dev/ttyS0.

Sure enough, when I try running the command
```
vishal@XXXX:~$ setserial -g /dev/ttyS0
/dev/ttyS0: No such device

```

The only solution seems to be a complete reboot of the machine. While this works, it seems highly inefficient, and overkill for this problem. I'm thinking there may be a power management option that's causing the problem, as I notice the problem almost always happens after I've been on battery power for a certain amount of time, but I don't know for sure.

Any help either re-activating the serial port or preventing it from deactivating in the first place would be really helpful. :-D

---

### Post by ceesnz on 2011-05-12
I don't have the answer for this because I seem to have  a similar problem.

I use a US robotics 56K fax external faxmodem on ubuntu 10.04 server. I can only use this modem if I reboot my server with the modem attached and turned on.
When the modem is turned off and subsequently turned back on it is no longer recognized.

I don't see the ttyS0: LSR safety check engaged! message though


```
ceesnz@XXX:~$ dmesg | grep ttyS0
[    0.877820] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.878160] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


ceesnz@XXX:~$ setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

```


Is there a way to re-activate the serial port without having to reboot ?

---

