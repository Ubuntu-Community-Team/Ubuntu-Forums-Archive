---
title: "Synaptics touchpad detected as Logitech Wheel Mouse"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by kenstad on 2007-09-09
Hi,
I have a recurring problem. Every once in a while my touchpad starts acting strangely - no left-clicks, and when I first touch the touchpad after startup it sticks on left-click pressed. I can plug in and use a USB mouse. (It doesn't matter if I start the computer with or without the USB mouse, the touchpad doesn't work as it should.) 

I know there have been similar threads, in the forum, but I think I have a very precise idea of where the problem is: My Synaptics touchpad is detected as a Logitech Wheel Mouse. Does anyone know how to deal with that? (I'm no expert, but the problem may be on the kernel driver level, which means that some developers have to get on it...) Here's the relevant information:

Ubuntu 7.04 - Feisty Fawn

**uname -r:**
2.6.20-16-generic

**tpconfig -i:**
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

**dmesg | grep Logitech:**
[   17.284000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
(There's no Logitech mouse connected!)

Can anyone help? (lspci and lsmod output attached)

---

