---
title: "Serial port problems"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by whilenski on 2007-03-12
Ok, here's my specs:

Dell D600 laptop
Ubuntu 6.10

I've installed minicom to use the serial port on my machine to connect to console ports on Cisco equipment, however, it fails to work.  The port works fine with Windows XP.  I've tried removing the Initialization String (didn't work), I've also tried to use the solution at [http://www.linuxquestions.org/questions/showthread.php?t=516635](http://www.linuxquestions.org/questions/showthread.php?t=516635) which was to run:
/bin/setserial /dev/ttyS0 baud_base 115200 auto_irq skip_test autoconfig
and 
stty crtscts -F /dev/ttyS0

however, my install of 6.10 doesn't have setserial installed on it (don't know how or why not).  Oh, and I've also set minicom to use /dev/ttyS0 and set it to 9600 8N1.

It appears others have had issues with this on HP laptops and with the USB to Serial dongles, however, to me it appears to be a larger issue with the Ubuntu install.  I know it worked in Hoary Hedgehog, Breezy Badger, and possibly on 6.06 LTS (I can't remember the last one for sure).

It doesn't seem like there is a lot of movement on this, but I want to get it out there so that it can possibly be fixed.  For me to be able to use this, I need a working serial port.

Any ideas?

Thanks in advance!

---

### Post by whilenski on 2007-03-13
Ok, I've solved the problem.

Seems that even after installing setserial I was having issues.  Turns out all I had to do was turn Hardware Flow Control to off in minicom.  I'm not sure if installing setserial helped out in this respect or not.

---

