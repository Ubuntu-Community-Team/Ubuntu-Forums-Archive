---
title: "patching usbserial"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by ksaling on 2005-10-16
I'm trying to apply the maxSize patch to usbserial as seen here:
[http://www.junxion.com/opensource/linux_highspeed_usbserial.html](http://www.junxion.com/opensource/linux_highspeed_usbserial.html)

This is Ubuntu Hoary 5.04 running 2.6.10-5-686 on my IBM Thinkpad T40.  

I type the following compile command:

root@jet:/usr/src/linux/drivers/usb/serial# gcc -D__KERNEL__ -I/usr/src/linux/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i386 -DMODULE -nostdinc -iwithprefix include -DKBUILD_BASENAME=usbserial -DEXPORT_SYMTAB -c usb-serial.c

I get the following errors...
```
In file included from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/linux/usb.h:15,
                 from usb-serial.c:15:
/usr/src/linux/include/linux/irq.h:71: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/irq.h:73,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/linux/usb.h:15,
                 from usb-serial.c:15:
/usr/src/linux/include/asm/hw_irq.h:28: error: `NR_IRQ_VECTORS' undeclared here (not in a function)
/usr/src/linux/include/asm/hw_irq.h:32: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/linux/usb.h:15,
                 from usb-serial.c:15:
/usr/src/linux/include/linux/irq.h:78: error: `NR_IRQS' undeclared here (not in a function)
usb-serial.c: In function `usb_serial_probe':
usb-serial.c:601: error: structure has no member named `lock'
```

I have linux-source-2.6.10 & linux-headers-2.6.10-5-686 installed.  

What am I missing here?

---

### Post by ksaling on 2005-10-19
[http://www.brandens.net/files/Sounds/FX/Animals/CRICKET.WAV](http://www.brandens.net/files/Sounds/FX/Animals/CRICKET.WAV)

---

