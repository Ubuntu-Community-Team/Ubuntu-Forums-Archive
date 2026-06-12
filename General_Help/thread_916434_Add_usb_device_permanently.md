---
title: "Add usb device permanently"
date: 2008-09-10
forum: General Help
---

### Post by Crangic on 2008-09-10
I'm currently every morning adding the following line of code so I'm able to use my usb modem.

```
sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280
```

How can I get this code to bootup of Ubuntu so I don't have to manually run this every time I restart the machine? I've seen /etc/modules mentioned but not sure what to add to that file. I'm using Ubuntu 8.04

---

### Post by wilbbe01 on 2008-09-10
I'm not sure as to where the "correct" place to put that would be.  You might try placing the code in /etc/rc.local

That might work for you.

---

### Post by Crangic on 2008-09-13
> **wilbbe01 said:**
> I'm not sure as to where the "correct" place to put that would be.  You might try placing the code in /etc/rc.local

That might work for you.

Thanks for the suggestion, will try that out.

---

