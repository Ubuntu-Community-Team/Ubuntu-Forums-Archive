---
title: "serial port not working"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by wanchai on 2006-11-27
Call me old fashioned, but I still need traditional serial ports. I have three machines with Edgy Ubuntu, the serial port works out of the box on two of them (Compaq Deskpro and Compaq Armada 7800), but not on the third (HP Compaq NC6000 laptop). The NC6000 can do it with COM1 in Windows, though. I am pretty sure that defective hardware and cable problems can be excluded, and the "far side", i.e. the Deskpro, is ok as well.

Right now, I'm just connecting two machines with a null-modem cable. Here is what I get:

> 
{dirk@wanchai}[/home/dirk]ls -l /dev/ttyS*
crw-rw-rw- 1 dialout 4, 64 2006-11-28 03:27 /dev/ttyS0
crw-rw-rw- 1 dialout 4, 65 2006-11-28 03:27 /dev/ttyS1
crw-rw-rw- 1 dialout 4, 66 2006-11-28 03:27 /dev/ttyS2
crw-rw-rw- 1 dialout 4, 67 2006-11-28 03:27 /dev/ttyS3

{dirk@wanchai}[/home/dirk]setserial -a /dev/ttyS0
/dev/ttyS0: No such device

{dirk@wanchai}[/home/dirk]sudo setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
        Baud_base: 115200, close_delay: 50, divisor: 0
        closing_wait: 3000
        Flags: spd_normal skip_test

{dirk@wanchai}[/home/dirk]sudo setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

{dirk@wanchai}[/home/dirk]echo blahblah > /dev/ttyS0
/dev/ttyS0: No such device.

{dirk@wanchai}[/home/dirk]sudo echo blahblah > /dev/ttyS0
/dev/ttyS0: No such device.

{dirk@wanchai}[/home/dirk]dmesg | tail -3
[17204867.876000] ttyS0: LSR safety check engaged!
[17204885.488000] ttyS0: LSR safety check engaged!
[17204901.476000] ttyS0: LSR safety check engaged!


Can anyone help, please? Thanks.

---

### Post by marcantonio on 2006-11-29
I am having the exact same issue with an HP nw8000.  I haven't found much yet, but here it is:

[LIST]
[*]I had no problems with this in Breezy or Dapper, just Edgy.

[*]The LSR error message seems to be a workaround for a buggy UART.

[*]On boot I noticed this message when udev was starting:
[/LIST]
```
udevd-event[3057]: wait_for_sysfs: waiting for: '/sys/devices/platform/i8042/serio3/serio5/bus' failed

```

---

### Post by wanchai on 2006-11-29
I posted the same request here:
[https://launchpad.net/distros/ubuntu/+ticket/2622]("https://launchpad.net/distros/ubuntu/+ticket/2622")

Not much help yet. Maybe you want to post your problem there as well.

---

### Post by wanchai on 2006-12-01
This has been reported as a bug:
[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74034]("https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74034")

As a workaround I'm using a cheapo USB->COM cable. Works ok.

---

### Post by chadd on 2007-05-04
I am having the same issue.  My serial port worked fine under Edgy, but when I upgraded to Feisty is stopped working.  I noticed the same messages about 'LSR safety check engaged!'.  Even when I get a UART assigned and the ouput of setserial -g looks ok, it still does not work to connect to a device with minicom.  This is something I really need, because this is my work laptop and I need to configure devices via serial.  I hope this gets fixed soon..

---

### Post by shields on 2007-05-04
I plugged in a serial mouse and installed ubuntu 7.04.  The mouse is not found, evidently as it's just sitting there.  Worked fine in Windows.  Any ideas? :confused: 

Thanks! :)

---

### Post by sshataka on 2007-06-04
Just figured out a workaround in Feisty, on an HP6000...

I disabled the IR port, and now my COM1 is working like a champ.  Looks like there's an IRQ conflict between those 2 devices, and the kernel isn't handling it properly.

And I thought I left IRQ issues behind when I upgraded from my 386...

---

