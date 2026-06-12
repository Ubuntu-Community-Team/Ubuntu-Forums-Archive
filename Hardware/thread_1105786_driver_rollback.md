---
title: "driver rollback"
date: 2009-03-25
forum: Hardware
---

### Post by lordpoee on 2009-03-25
greetings all

I was using the rt2500pci wireless driver
I decided to experiment with the ndiswrapper driver...

well it was slow as crap...stable...but slow as crap.

I would very much like to switch back to the rt2500pci driver...

The driver is obviously already on the system, how do I tell ubuntu to use the rt2500pci driver instead?

I am using ubuntu 8.10

[SOLVED]

Seems I am getting n the habit of answering my own questions :)

Okay, if you ever have this problem simply use modprobe to fix things.

```


sudo modprobe -r ndiswrapper
sudo modprobe -i rt2500pci
sudo depmod


```
now right click the wireless applet, disable wireless then renable.

Problem solved. :)

If someone knows a better way please post.

---

