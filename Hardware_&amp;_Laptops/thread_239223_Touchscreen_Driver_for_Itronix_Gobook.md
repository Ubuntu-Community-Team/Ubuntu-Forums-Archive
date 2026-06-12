---
title: "Touchscreen Driver for Itronix Gobook"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by Speedboxer on 2006-08-18
Hello, I have a Itronix Gobook IX250 Notebook Computer. It has a Gunze USB Universal Point Device (Touchscreen) on it. I installed Dapper Drake onto it and I'm looking for a driver for the Touchscreen. Anyone know of a driver that will work with this Touchscreen?

Thanks,
Speedboxer :)

---

### Post by Speedboxer on 2006-08-21
Is there a way to get my touchscreen to be detected as a Joystick? Or at least trick Ubuntu into thinking it's a Joystick?

Thanks,
Speedboxer

---

### Post by rickshawallah on 2006-10-12
very sorry but i can't really help you except to say that i also have a similar itronix 250 - mine has a celeron 850 - and am just in the process of trying to set it up - first attempt hung - any little pointers to set me on my way gratefully received and then perhaps i can join the search for the touch screen fix! I hasten to add that i am not a linux whiz or even a computer whiz but i can be methodical which i guess which is half the battle! all the best, ollie

---

### Post by attrezzo on 2007-03-04
I have some ideas here on why it's not working. I have a gobook as well but I run gentoo on it. I've got to say first of all this laptop has lots of pointer problems. When you get it loaded with X11 you might notice that the pointer freezes occasionally and won't let you move the pointer. I think this is cause of the synaptics touchpad. I haven't heard a whole lot about this but if it happens don't be surprised.

The second thing is that the touchscreen is detected as usb but never sets up an event interface or (for that matter) any interface. I'm starting to wonder if the USB acts as a USB to serial device and that the gunze touchscreen is actually a serial touchscreen rigged through the USB? It doesn't make much sence but the ts on the gobook is more or less the same as the earlier models and it might have been some screwed up effort to save money. Either way I haven't found a way to get it detected in the kernel. You might try modifying the GunzeTS drivers although they are VERY old. (not made to compile in 2.6 kernels).

---

### Post by haberb on 2007-09-15
I recently did a network install of an older version of ubuntu and upgraded to fiesty on my gobook ix250. I thought that the touchscreen driver would definitely not work out of the box. It looks like the touchscreen was recognized as a wacom tablet though. (that's what it seems to say in the x conf). I have to I can move the cursor around, but it's not accurate. my horizontal (x?) movement is off about an inch, and my vertical movement is flipped. I'm thinking that maybe some simple changes to the wacom setup could get me close to a working setup. Anyone an expert with wacom drivers?

---

### Post by haberb on 2007-11-22
Success! Following the directions at [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html) I am now able to use my goBook touchscreen. I had to flip the y axis, and it still needs some additional fine tuning, but i'm very happy with it's usefullness so far.

---

