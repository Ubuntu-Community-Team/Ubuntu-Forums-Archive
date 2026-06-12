---
title: "Ipod not seen by Ubuntu"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by mattwho on 2007-04-05
I've searched the forums and google but don't see a problem like mine. I plug in my ipod Nano and it charges but does not display the "Do not disconnect" message.

dmesg shows nothing new after plugging it in and lsusb does show it as well.

---

### Post by teaker1s on 2007-04-07
while I'm not a ipod owner, my suggestions- I'm wondering if your issue is purely a case of not mounting.
As I understand it your saying lsusb shows it?

also see if you can see it in

```
fdisk-l
``` 
If you can't see it to manually mount it, I'm wondering if **gtkpod** application would mount it?

---

### Post by mattwho on 2007-04-07
resetting the ipod solved it

---

