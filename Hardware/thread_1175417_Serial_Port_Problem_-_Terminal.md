---
title: "Serial Port Problem - Terminal"
date: 2009-06-01
forum: Hardware
---

### Post by Hinomura on 2009-06-01
Hi, (first, sorry for my english)
This is the problem:

I need to connect a GPS receiver to a linux system. This receiver is sending ASCII strings constantly, and I should see this signal with any terminal program, but I cant.

I started using USB-RS232 conver adapters, but I dont get results. The problem is that Im now in a PC with Serial Port, and I cant still see nothing in the terminal. Im usin GTKterm (minicom tested too), and Im not receiving nothing. Im using the same config that works in hyperterminal, in windows.

I checked BIOS and there the port and IRQ for serial port is :  3F8H / IRQ 4 and using setserial:

hinochino@AMD2800:/$ setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

Then, I supose that the port and IRQ are the same in hardware and drivers.

Opening this file about serial port I can see how transfer rise when I press keys in GTKterm but obiously the receive transfer is 0.

hinochino@AMD2800:~$ sudo cat /proc/tty/driver/serial
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 **tx:48** rx:0
1: uart:unknown port:000002F8 irq:3
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3


I dont have any more ideas, Im losing something?

Thanks.

---

