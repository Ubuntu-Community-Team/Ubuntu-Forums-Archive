---
title: "Serial scanner: Dexxa Flatbed 4800 with Feisty"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by takeawaydave on 2007-05-25
Hi All - here goes my very first post.... sit back and enjoy  :popcorn:


I have a pretty ancient looking serial scanner that xsane has is not recognised by feisty. Not tooo surprising since itt is not on the supported hw list.

However I would very much like to get it working and not let it go to waste. It was working on windows and I just migrated my mum over to ubuntu (she's very happy but unfortunately she said she can't really see her self becoming part of The Community :(   )

I have been using Linux for about 4 years but not every day so need a bit of help here. 

Cheers....

---

### Post by takeawaydave on 2007-05-25
A little more infor:
```

jackie@squirrel:~$ cat /var/log/dmesg | grep tty
[   22.310322] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.310492] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.311159] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.311405] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.102798] usb 2-2: cp2101 converter now attached to ttyUSB0
```

and:

```
jackie@squirrel:~$ cat /proc/tty/drivers 
/dev/tty             /dev/tty        5       0 system:/dev/tty
/dev/console         /dev/console    5       1 system:console
/dev/ptmx            /dev/ptmx       5       2 system
/dev/vc/0            /dev/vc/0       4       0 system:vtmaster
rfcomm               /dev/rfcomm   216 0-255 serial
usbserial            /dev/ttyUSB   188 0-254 serial
serial               /dev/ttyS       4 64-111 serial
pty_slave            /dev/pts      136 0-1048575 pty:slave
pty_master           /dev/ptm      128 0-1048575 pty:master
pty_slave            /dev/ttyp       3 0-255 pty:slave
pty_master           /dev/pty        2 0-255 pty:master
unknown              /dev/tty        4 1-63 console

```

and the following at the end of dmesg output:

```
[ 2807.936000] ppdev0: registered pardevice
[ 2807.976000] ppdev0: unregistered pardevice
[ 3266.000000] ppdev0: registered pardevice
[ 3266.048000] ppdev0: unregistered pardevice

```

Which googling has led me to believe is caused by a parallel device - maybe scanner is parallel and NOT serial as I thought.... not too good with these old proprietary sockets....

---

### Post by takeawaydave on 2007-05-27
No one? Any one?

---

### Post by trampolando on 2007-05-29
Same scanner, same problem

---

### Post by trampolando on 2007-12-30
using the driver
Artec AS6E
the scanner is moving, and making some noise, but I'm not gettin it working correctly

---

