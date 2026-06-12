---
title: "[SOLVED] Serial Port Problem?"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by canclan on 2008-04-16
Hello!
I am trying to get a piece of windows software to run under the latest WINE in Gutsy.  The program runs but when I try to use the serial port (ttyS0/com1) it returns the error:
> Can't Open Serial Port
Last Error : File not found

When I type 

> dmesg | grep tty

I get

> [   77.685502] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   77.685974] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   77.686820] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.704000] ttyS0: LSR safety check engaged!
[   29.704000] ttyS0: LSR safety check engaged!
[   29.704000] ttyS0: LSR safety check engaged!
[   29.708000] ttyS2: LSR safety check engaged!
[   29.708000] ttyS2: LSR safety check engaged!
[   29.708000] ttyS2: LSR safety check engaged!
[   33.484000] ttyS0: LSR safety check engaged!
[   33.492000] ttyS2: LSR safety check engaged!
[   34.408000] audit(1208366509.633:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4982 profile="/usr/sbin/cupsd"
[  422.972000] ttyS0: LSR safety check engaged!

but when I enter:

> setserial -g /dev/ttyS[0123]

I get

> /dev/ttyS0: No such device
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2: No such device
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3


So is ttyS0/com1 there or not?  Does anyone know or have any experience with this problem?  The laptop is a HP NC8000.

Thanks in advance!

---

### Post by Gabn on 2008-04-18
i had a look at setserial and i'm not sure what it has to do with wine... 


In your wine folder .wine in your home folder 
you want to go into dos devices 

then try ln -s /dev/ttyS0  com1 

you need to tell wine where your com ports are... 

( i haven't exactly gotten this to work for me but yeah i'm working on serial access in wine. )

[http://winehq.org/site/docs/wineusr-guide/misc-things-to-configure#AEN408](http://winehq.org/site/docs/wineusr-guide/misc-things-to-configure#AEN408)  more information here 

My current problem is 100% cpu usage when the com port is active...

---

### Post by canclan on 2008-04-18
> **Gabn said:**
> i had a look at setserial and i'm not sure what it has to do with wine... 


In your wine folder .wine in your home folder 
you want to go into dos devices 

then try ln -s /dev/ttyS0  com1 

you need to tell wine where your com ports are... 

( i haven't exactly gotten this to work for me but yeah i'm working on serial access in wine. )

[http://winehq.org/site/docs/wineusr-guide/misc-things-to-configure#AEN408](http://winehq.org/site/docs/wineusr-guide/misc-things-to-configure#AEN408)  more information here 

My current problem is 100% cpu usage when the com port is active...


Thanks for the response!  

100%?  OUCH!  Yeah, that might be a problem!  I am sorry I don't know enough about linux serial port problems to offer a suggestion.

Setserial doesn't have anything to do with wine, it just allows one to query the port for information (with a bunch of options).  It apparently allows you to set (via software driver) some serial port options.   Perhaps your answer lies in there somewhere? 

Yes, I believe that command puts com1 into the dosdevices list  (which it appears to have done).  I also added the user (me) to the group which allows access to the port.   I am pretty sure I am only missing some small detail, I just can not find or figure out what it is!  I *think* wine knows where the port is, I think *maybe* the kernel is not allowing the connection.

---

### Post by canclan on 2008-04-20
Problem resolved!

It turns out that it is a (relatively) common problem with HP laptops and newer versions of Ubuntu.  The solution is to go into the BIOS and shut off the IR port.  There is a conflict between the IR port and com1.

So there you have it - twenty hors of troubleshooting for a 2 minute solution!

I hope someone else can be helped by this solution!

canclan.

---

