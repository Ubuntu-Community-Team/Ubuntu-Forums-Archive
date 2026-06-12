---
title: "Xbox 360 wireless controller crashes Gnome."
date: 2008-09-26
forum: Hardware
---

### Post by Nonni on 2008-09-26
Hi,
When I connect my wireless Xbox 360 controller, it is recognized by xpad, this is what I see in dmesg:
> 
[   15.090368] input: Xbox 360 Wireless Receiver as /class/input/input5
[   15.121618] input: Xbox 360 Wireless Receiver as /class/input/input6
[   15.133651] input: Xbox 360 Wireless Receiver as /class/input/input7
[   15.141648] input: Xbox 360 Wireless Receiver as /class/input/input8
[   15.149623] usbcore: registered new interface driver xpad
[   15.149627] xpad: X-Box pad driver

After I plug it in, I can move the gnome crashes to the login screen and I can move the mouse pointer with the left analog button. Pressing any button on the controller makes gnome crash back into the login screen.

If I go to console(ctrl+alt+f1) and run jstest /dev/input/js0 I get 'normal' output.

I want to use the gamepad for games, not as a mouse substitute in gnome :(.

Anyone know how to make the controller behave normally ?

I'm running the intrepid ibex alpha.

Thanks.

---

