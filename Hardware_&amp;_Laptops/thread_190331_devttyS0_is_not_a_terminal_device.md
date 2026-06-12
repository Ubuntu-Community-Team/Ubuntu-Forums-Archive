---
title: "/dev/ttyS0 is not a terminal device"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by siska on 2006-06-06
Hi,
I'm using the latest kubuntu, but I had the same issue with an ubuntu flight sometimes ago.

I'm trying to send a file by using the kermit program, sudo apt-get install ckermit, by using the serial port ttyS0 on my laptop, toshiba satellite 4090.

It should be said that my serial port and my kermit worked fine with debian and freebsd (I used 6.1 before installing kubuntu).

*sudo kermit -y kermit.ini -s myfile.crc*
_/dev/ttyS0 is not a terminal device_
?SET SPEED has no effect without prior SET LINE

Some system infos:

*kermit.ini*
set line /dev/ttyS0
set carrier-watch off
#set flow-control rts/cts
set flow-control none
set speed 57600

(I installed setserial by using sudo apt-get install setserial)
*sudo setserial /dev/ttyS0*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

*ls -al /dev/ttyS0*
crw-rw---- 1 root dialout 4, 64 2006-06-06 03:44 /dev/ttyS0

*cat /etc/serial.conf*
/dev/ttyS0 port 0x3f8 irq 4 autoconfig

*dmesg | grep ttyS*
[   28.507152] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.518884] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

I see that I cannot use the serial port as a normal user, I need to use sudo, but that's not a main issue actually.

The issue is that the ttyS0 cannot be used.

I'm not sure if another application is using it but I don't know where to look.

I don't know what to do ](*,) 

Any help would be appreciated,

Thanks, :)

p.s.
I attach a copy of my xorg.conf

---

### Post by Ptero-4 on 2006-08-14
I have similar issues. Maybe the ttyS0 device file that ships with Dapper 6.06 is faulty.

---

