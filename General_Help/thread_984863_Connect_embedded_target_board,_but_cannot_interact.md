---
title: "Connect embedded target board, but cannot interact with serial port"
date: 2008-11-17
forum: General Help
---

### Post by leeyee on 2008-11-17
Hi guys,

I want to do some embedded development under Ubuntu, the target board is s3c2410 ARM. However, i encountered a problem with serial port communication.

That is, after i set up serial port correctly in minicom, **i can exactly see the booting information of the board. However, i cannot do any other except that!** I cannot press keys in minicom, and either cannot see the shell. It seems that the serial port is read only, i can't control the board. Not only minicom, i have the same problem in kermit, cu and gtkterm.:(

Embedded linux has been burnt into the board originally, and I've tested the board in another XP machine, it works fine in the super terminal, so i'm sure the board is fine. 

and here are some information you may interested in:
```
liye@dsplab-> dmesg | grep tty
[   54.946897] console [tty0] enabled
[   56.608924] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.609329] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```
```
liye@dsplab-> ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2008-11-17 14:07 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2008-11-17 12:30 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2008-11-17 12:30 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2008-11-17 12:30 /dev/ttyS3

```

Thanks for your help or any advice! I do NOT want to develop a embedded linux under windows.:(

---

### Post by leeyee on 2008-11-17
Nobody has the same problem? I've searched a lot, and do see some people have this problem too. However, none of them has solution. Should i report a bug on this?

---

