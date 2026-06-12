---
title: "Serial port only work after wake-up from hibernation!"
date: 2009-05-09
forum: Hardware
---

### Post by mirozo on 2009-05-09
I need to use my serial port on my Thinkpad T22. I just installed Xubuntu 9.04 and I first try to make it work with python pySerial module, did not work.. I than try to make it work with gtkTerm without success. I know the serial port work on this machine because it work just fine with hyperTerminal on WinXp.

Here what I have:


[FONT=Lucida Console]dmesg | grep tty

[    0.004000] console [tty0] enabled
[    7.672574] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


setserial /dev/ttyS0

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4


cat /proc/tty/drivers

/dev/tty             /dev/tty        5       0 system:/dev/tty
/dev/console         /dev/console    5       1 system:console
/dev/ptmx            /dev/ptmx       5       2 system
/dev/vc/0            /dev/vc/0       4       0 system:vtmaster
rfcomm               /dev/rfcomm   216 0-255 serial
usbserial            /dev/ttyUSB   188 0-253 serial
serial               /dev/ttyS       4 64-111 serial
pty_slave            /dev/pts      136 0-1048575 pty:slave
pty_master           /dev/ptm      128 0-1048575 pty:master
unknown              /dev/tty        4 1-63 console[/FONT]


I've try "setserial autoconfig" many times without success. What is weird is everything seems normal but when I try to make it work in gtkTerm, the serial port is dead eventhough, their is no error logged for ttyS0 anywhere I've looked. Then, by luck, I've put the laptop in hibernation and after the "wake-up", the serial port ttyS0 did work in gtkTerm. I then rebooted the laptop and again, the serial port in gtkTerm was dead and after an hibernation-wake-up, the serial port did come alive again...

Anyone know what's going-on???

---

