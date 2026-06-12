---
title: "Upgrading to Which Kernel for Hardware (TV Tuner)?"
date: 2016-04-05
forum: Hardware
---

### Post by sadeghbiology on 2016-04-05
I'm currently using kernel 3.16.0 version for 14.04 LTS. I'm going to buy a TV tuner and all of them are made for Windows as default.
Is upgrading the kernel going to improve the chance of hardware compatibility?
I'm not much of an expert in Ubuntu but a big fan of free software movement so I ain't going to install Win on my laptop :)

---

### Post by Bucky Ball on 2016-04-05
Welcome. Virtually no TV card, or hardware device really, is marked as 'Linux compatible' so ...

I have an EZYCap USB tuner. Plug an antennae cable into it, that into the USB of the computer, install Me-TV and you're goggling. :)

How do you know whatever hardware you buy is not going to work out-of-the-box with the kernel you already have? My EZYCap took some fiddling to get working in 12.04 LTS. Worked off the bat in 14.04. 

As long as the card isn't very new (released tomorrow!) there's a good chance it will work fine with what you already have. Plug it in. Open a terminal straight away and type:

> dmesg

... then hit return. What do you see about the card at the bottom of the screen? It's not so much about the plastic casing, but about the chip inside it. Mine has a Realtek, even though the label on the plastic casing says EZYCap. When I plug in and run dmesg, I get:

```
Realtek RTL2832 successfully attached
[17443.993937] usb 1-10: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
```

---

### Post by deadflowr on 2016-04-05
Look at the linuxtv wiki on tuners that work out of the box.
[https://www.linuxtv.org/wiki/index.php/Hardware_Device_Information](https://www.linuxtv.org/wiki/index.php/Hardware_Device_Information)

There are a lot of fully functional tuners out there.
You need to determine what kind you need.
And what kind you need also depends upon where you live.

Example, I need one that supports ATSC. (For USA over the air broadcasts)
You might need one that supports DVB-C, DVB-T or -S or something else.

---

