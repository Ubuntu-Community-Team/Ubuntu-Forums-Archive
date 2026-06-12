---
title: "Hardy Heron - USB Ports dead"
date: 2008-12-25
forum: Hardware
---

### Post by jessekaboom on 2008-12-25
I switched to Linux just recently, so I apologize for not knowing much of the lingo or how to use the advanced functions of the OS, as I was a Windows slave for sixteen years of my life.

I've been running Hardy Heron for about three months now with no real problems, but suddenly my USB ports have stopped working - devices that had worked fine with them before aren't even recognized, like flash drives or my external hard drive. When I plug them in, the little 'connected' light on the devices won't even light up. The devices worked fine for the last three months, but today the USB ports suddenly decided to stop working. They're also USB 2.0 ports, if that helps.

Has anything like this happened to anyone else? If it will help, I'm using a Compaq Presario SR2006NX.

Any thoughts, or bits of code?

Thanks, 
-j

---

### Post by taurus on 2008-12-25
Open a terminal and run

Applications -> Accessories -> Terminal
```
lsusb
```
Now, plug it in and see what happens.

---

