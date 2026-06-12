---
title: "Serial port error"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by tordan on 2007-09-18
I installed "Wine" in order to operate a data collection
program for our temperature datalogger unit at work, but I'm having some
problems.

When the program ("Data Acquisition" by Extech Instruments) is booting
up it comes up with :"COM Port ERROR: Unexpected internal error" then proceeds to open the
program after I hit "OK". The only problem I can detect is that it will
not connect with the device via the motherboard's built in Serial port. I have changed the location that the program looks for the port in (com1-com4) and still no luck finding the
device (or at least communicating with it). Is there a component of Wine
that I need to change or install to get it to recognize the port system
for Lynux?

Let me know if you need more info.

Thanks in advance.

(I actually posted this to the "Beginner's" section and received no response, sorry for the duplicate postings.)

---

### Post by tordan on 2007-09-18
I found a post that recommended a bunch of actions I didn't quite follow. It did suggest the code to get this:

```

user@user-desktop:~$ setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3

user@user-desktop:~$  dmesg | grep tty
[   16.065546] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.068906] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.104529]   hash matches device ttyd8
[   16.104559]   hash matches device ttyab

```

---

### Post by tordan on 2007-09-19
I still haven't had any luck fixing this problem. Someone has been trying to help me at this other thread: [http://ubuntuforums.org/showthread.php?t=553256]("http://ubuntuforums.org/showthread.php?t=553256")

Please, if you know of any way of trouble shooting this problem... help...

---

### Post by gasansat on 2007-10-18
Hi
any one have install this PCI card with 8 port out before  
this error masage  detected caps 00000700 should be 00000100
and this all information
root@dream-desktop:/lib# dmesg | grep ttyS
[17179571.000000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.004000] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.004000] ttyS4: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.0: ttyS4 at I/O 0xec00 (irq = 209) is a 16C950/954
[17179571.004000] ttyS5: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.0: ttyS5 at I/O 0xec08 (irq = 209) is a 16C950/954
[17179571.004000] ttyS6: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.0: ttyS6 at I/O 0xec10 (irq = 209) is a 16C950/954
[17179571.004000] ttyS7: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.0: ttyS7 at I/O 0xec18 (irq = 209) is a 16C950/954
[17179571.004000] ttyS8: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.1: ttyS8 at I/O 0xe800 (irq = 217) is a 16C950/954
[17179571.004000] ttyS9: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.1: ttyS9 at I/O 0xe808 (irq = 217) is a 16C950/954
[17179571.004000] ttyS10: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.1: ttyS10 at I/O 0xe810 (irq = 217) is a 16C950/954[17179571.004000] ttyS11: detected caps 00000700 should be 00000100
[17179571.004000] 0000:03:00.1: ttyS11 at I/O 0xe818 (irq = 217) is a 16C950/954
a wait any kind help
:confused::confused:

---

