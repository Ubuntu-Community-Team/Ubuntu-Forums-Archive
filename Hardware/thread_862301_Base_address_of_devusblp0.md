---
title: "Base address of /dev/usb/lp0?"
date: 2008-07-17
forum: Hardware
---

### Post by swharden on 2008-07-17
I understand that a standard onboard parallel port is usually /dev/lp0 and has a base address of 0x378.  I have a laptop and a Belkin USB printer adapter (pictured below).  When plugged in, it shows up as "/dev/usb/lp0".  I want to be able to set/read the state of the pins like I would a standard parallel port.  How can I determine the base address of this device? (ex: 0x378 )  I wish to use the following python script to manually control the state of the pins.

```
#!/usr/bin/python
import sys, time, os
import portio

# acquire permission for I/O on lp0
portio.ioperm(0x378, 1, 1)

# toggle for ever the data lines of lp0
data = 0
while 1:
  lp0in = portio.inb(0x378)
  portio.outb(data,0x378)
  print 'read %x from lp0, written %x to lp0' % (lp0in,data)
  data = ~data & 0xff
  time.sleep(1)
```

[IMG]http://www.systemaxdev.com/productmedia/htmlimages/cten/belkin/parallel.jpg[/IMG]

---

### Post by rapsodia on 2009-11-05
hi, 

Did you ever find out how to look for the base port of address ?

---

### Post by rapsodia on 2009-11-05
I found this it might be useful to you

6.1 The parallel port

The parallel port's base address (called ``BASE'' below) is 0x3bc for /dev/lp0, 0x378 for /dev/lp1, and 0x278 for /dev/lp2. If you only want to control something that acts like a normal printer, see the Printing-HOWTO. 


[http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html#s1](http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html#s1)

---

### Post by Dwarrel on 2010-03-03
Hi i would like to repeat this question. Not making a new thread because I'm looking for an identical answer. 

Is it possible to emulate or change /dev/usb/lp0 to /dev/lpx.

---

