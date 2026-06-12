---
title: "Listen on serial port to find baud-rate"
date: 2011-07-14
forum: Hardware
---

### Post by stevejesus on 2011-07-14
Hi,

I have a device that I need to connect to over serial but I don't know the baud-rate, parity, etc.

If I hook the device to my laptop, is there a tool that I can use to listen and guess?

Is there a utility that will try and guess?

Thanks

---

### Post by Vansch76 on 2011-07-14
Google realterm

it can be downloaded from sourceforge.
its a windoz program but it says it will run under wine.

you can set the different baud rates in the program and see if your
device will talk to it.

what kind of device is it anyway?

Vanessa

---

### Post by stevejesus on 2011-07-15
Point Of Sale.

I think I can use Cutecom in Linux for that or even Hyper-Terminal in Windows.  I'm guessing that since serial devices don't seem to 'announce' themselves, I need a program that will automatically try all configurations until it receives data.

---

