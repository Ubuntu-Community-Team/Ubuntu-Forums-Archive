---
title: "USB to Serial port Symbolic Link"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by jellystones on 2008-01-01
Hi,

This is not very Ubuntu related (more general linux related but there is such a great community here) 

I am in the middle of a project for which I need to access a USB GPS device. To make a long story short, java has poor USB support and my project would be much easier if I was working with a GPS device via a Serial cable.

So my question is, is it possible to redirect the input from the usb device (like /dev/usb) to a serial input (using a symbolic link), to trick Java into thinking it is working with a Serial cable?

Does this even make sense????

---

### Post by kidders on 2008-01-04
Hi there,

In general, anything in /dev with the characters "tty" in its name is a serial device interface. Depending on how it's been configured, the Linux kernel exposes serial interfaces to lots of USB devices ... for example, phones & other modem-like devices typically get called things like ttyUSB0 or ttyACM0.

If you're in doubt, I can tell you how to check, but to my knowledge, all Ubuntu kernels include virtually every available USB serial interface ... in which case, my guess is you're out of luck :-( (I'm assuming you've already taken a look at what your dmesg has to say about your GPS, and not seen anything encouraging.)

If I were you, I'd take a look around for information on how other users of similar hardware have managed to get it to talk to Linux and/or develop software with it. Hopefully you're particular model isn't too uncommon. In a perfect world, you'd happily discover that your hardware manufacturer has already written an open source serial converter to plug into your kernel. Somehow, I doubt that though!

If you're *really* desperate, I wonder if a hardware-based USB/serial converter (rather than a software-based one) would be worth investigating. More realistically, perhaps you might take a look at implementing something in C that can perform a few basic operations on your GPS over the standard USB interface, and invoking the code using JNI. That way, you could side-step Java's shortcomings in the area. Unfortunately, I'm not even *close* to familiar enough with the low-level USB world to be of any practical help. With any luck, you are ... or someone you know is!

**Edit:** Lol... I forgot to actually answer your question!! There is no way to use symlinks to turn a USB interface into a serial one. I'm not too sure what you have in mind, but serialising a USB interface to a device requires a little coding (and is not always possible).

---

