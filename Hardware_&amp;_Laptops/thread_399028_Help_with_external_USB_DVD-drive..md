---
title: "Help with external USB DVD-drive."
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by ubuntnoob on 2007-04-01
I have a BenQ external USB DVD-RW drive that I cannot get working.
I plug it in and it does not seem to recognized.  I have tested the USB port with a flash drive and it is found and mounted automatically, but for the DVD drive nothing.

I am using Ubuntu Edgy on a desktop PC.

Any help would be appreciated.

Thanks.

---

### Post by teaker1s on 2007-04-02
some dvd drives need driver, some don't.
Now the first port of call would be terminal
```
lsusb
``` post output

I've subscribed to this thread and will try to help you find an answer-I may not be able to reply today, but I will reply:KS

---

### Post by Sebastral on 2007-04-12
I had the same problem. Wouldn't turn up with lsusb. Connected a different usb-cable and now it does :roll:

---

### Post by teaker1s on 2007-04-12
also be aware that sometimes devices on same hub =problem
my dvd drive won't mount if on same hub as printer

---

