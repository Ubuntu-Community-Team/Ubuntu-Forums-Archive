---
title: "OKI14ex - usblp0 problem"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by entereczek on 2006-10-01
Sometimes when I'm trying to print to my OKIPage14ex printer I get error like this...
```
Oct  1 20:17:38 localhost kernel: [17180374.556000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x06BC pid 0x000B
Oct  1 20:18:53 localhost kernel: [17180449.920000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
Oct  1 20:18:55 localhost kernel: [17180451.020000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -84
Oct  1 20:19:16 localhost kernel: [17180472.036000] printk: 207 messages suppressed.
Oct  1 20:19:16 localhost kernel: [17180472.204000] usb 3-1: USB disconnect, address 4

```
To solve i'm turning on and off my printer but I lose document sent to printer and I have to print it once more time...
It happends when I'm printing for example 3 documents...
First and second is ok. But third I get error "nonzero read/write..." and on my OKI I get "PCL DATA"... And its not printing...

Regards
Entereczek

---

