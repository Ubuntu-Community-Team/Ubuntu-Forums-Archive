---
title: "Opensource elo touchscreen drivers and inputattach utility"
date: 2008-10-17
forum: Hardware
---

### Post by sternocera on 2008-10-17
Hello,

I'm trying to get the kernel's elo touch serial driver working with xubuntu 8.04:

[http://www.gelato.unsw.edu.au/lxr/source/drivers/input/touchscreen/elo.c](http://www.gelato.unsw.edu.au/lxr/source/drivers/input/touchscreen/elo.c)

I've been in contact with the driver's author, Vojtech Pavlik. 

It is reliant on a utility that he also wrote which is mostly used for serial joysticks, inputattach. Here's what I do:

> sudo modprobe serport 
> sudo modprobe elo
> sudo inputattach --elotouch /dev/ttyS4
>

The driver's author advises that once I do this, the device should be visible in /proc/bus/input/devices. However, it is not. I'm quite certain of this.

I have got this touch screen working, but only with the proprietary driver, that comes with a dirty big .so . This in unacceptable. 

The author suggested it might also have something to do with my particular touchscreen using the wrong protocol. I confirmed that I was using the correct, default 10-byte protocol, so that eliminated that possibility. Also, I was sure to disable the proprietary drivers when I attempted all this, lest there be some sort of conflict.

Does anyone have any experience with this? Any advice that you guys could offer would be hugely appreciated, as this is a high priority project for me. Even if you took a stab in the dark and suggested something that only had a slim chance of working, I'd still like to hear it!

Thanks,
Sternocera

---

### Post by sternocera on 2008-10-17
Vojtech advised me by e-mail that I should attempt to "inputattach -elo4", and see if the (incorrect) device appeared under /proc/bus/input/devices - apparently, it should, regardless of whether or not an Elo touch screen is even present. It did not appear there, which suggests a problem with my system. The question is, what problem, and how can it be solved? 

Thanks,
Sternocera

---

