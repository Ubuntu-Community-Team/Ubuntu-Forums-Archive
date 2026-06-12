---
title: "serial port renumbered and no longer working with os upgrade"
date: 2011-05-29
forum: Hardware
---

### Post by goatbar on 2011-05-29
Hi all,

I just updated a 9.04 machine all the way to 11.04 in the last two days.  This machines job is to log serial data from what was the second serial port on the motherboard: /dev/ttyS1 at 38400 8N1.  That device name now fails and after much digging, I see that serial ports have been renumbered??? I've done "apt-get purge modemmanager".  Here is what I now get for the serial ports from dmesg (I wish I had kept this from before I started the update process)

Ubuntu 9.10:

> May 27 12:01:54 tide3 kernel: [    3.404727] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 27 12:01:54 tide3 kernel: [    3.405117] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 27 12:01:54 tide3 kernel: [    3.405313] 0000:04:00.0: ttyS1 at I/O 0xdcc8 (irq = 16) is a 16550A
May 27 12:01:54 tide3 kernel: [    3.405411] 0000:04:00.0: ttyS2 at I/O 0xdcd0 (irq = 16) is a 16550A
And now with ubuntu 11.04:

> 
dmesg | grep ttyS
[    2.035886] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.394380] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.414760] 0000:04:00.0: ttyS4 at I/O 0xdcc8 (irq = 16) is a 16550A
[    2.435030] 0000:04:00.0: ttyS5 at I/O 0xdcd0 (irq = 16) is a 16550A

var/lib/setserial# cat autoserial.conf
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
#KERNEL
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test
/dev/ttyS4 uart 16550A port 0xdcc8 irq 16 baud_base 115200 spd_normal skip_test
/dev/ttyS5 uart 16550A port 0xdcd0 irq 16 baud_base 115200 spd_normal skip_test
Is there anything else that I need to do to get the serial port working again?  I've tried listening to ttyS[045] with this script and minicom to see the 2 NMEA messages per second, but I am getting nothing.  Suggestions? 

```

#!/usr/bin/env python
import serial
ser = serial.Serial(port='/dev/ttyS4', baud= 38400, timeout=timeout)
line = ser.readline()
print 'line:',line

```And why were the serial ports renumbered?

```
for dev in ttyS{0,1,2,3,4,5}; do
   setserial -v -a /dev/${dev}
done

/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

/dev/ttyS1, Line 1, UART: unknown, Port: 0x02f8, IRQ: 3
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

/dev/ttyS2, Line 2, UART: unknown, Port: 0x03e8, IRQ: 4
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

/dev/ttyS3, Line 3, UART: unknown, Port: 0x02e8, IRQ: 3
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal

/dev/ttyS4, Line 4, UART: 16550A, Port: 0xdcc8, IRQ: 16
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

/dev/ttyS5, Line 5, UART: 16550A, Port: 0xdcd0, IRQ: 16
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

```System info: Dell 745 small form factor w/ a Intel Core2 CPU 6300

uname -r: Linux  tide3 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by goatbar on 2011-06-01
Resolved.  /dev/ttyS1 became /dev/ttyS4 - the two ports on the extra card got bumped up.  It's hard to debug remotely with a device that sends data sporadically with intervals that can be as long as hours between.

I really dislike that the ports got renumbered.  Additionally, my other data logger that is at 10.10 was showing what I thought was the same issue, but a hard power cycle brought the serial port

---

