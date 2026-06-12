---
title: "Serial Port Disabled??"
date: 2011-09-08
forum: Hardware
---

### Post by mohitdaksh on 2011-09-08
Are serial ports disabled by default on Ubuntu?

I have never used the serial ports(DB9) on my PC before. Now I wanted to use one for my [arduino]("http://ubuntuforums.org/www.arduino.cc/en/Main/ArduinoBoardSerialSingleSided3") board but saw that the IDE displays only two ports which are my front USB ports. No mention of the Serial ports at the back of the CPU cabinet. 

'When I ran the command ```
dmesg | grep tty

``` I got the following output:
```
[    0.000000] console [tty0] enabled
[    0.245992] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.246213] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.246858] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.247093] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

```Does anybody have an idea how to get my serial port to work?

---

### Post by larryfeltonj on 2011-09-16
I'll be going through the same process soon for the same reason (setting up arduino).  I found a few links searching the web (although I haven't tried using them yet).

Here is one using a usb->serial adaptor

[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

I don't know if it'll work for you (or me), but it's worth a shot.

---

