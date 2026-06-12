---
title: "Get model of monitors plugged to the computer"
date: 2010-07-19
forum: Hardware
---

### Post by BorrajaX on 2010-07-19
&#65279;Hello everyone!

I am currently developing an small program in Python and at a certain point, I need to do some &#8220;stuff&#8221; depending on the monitors that are connected to the computer. I have an intel vga card with two outputs. I want to do &#8220;something&#8221; if one of the screens connected to the output is a &#8220;Dell&#8221;, another &#8220;something&#8221; if one of the monitors is a &#8220;Nec&#8221; and another &#8220;something&#8221; if both monitors are connected.

So the question is: Is there any way to get the vendor/model of the monitors currently connected to the computer?

I did a little bit testing. I plugged both screens to my vga card (the Nec to the HDMI output and the Dell to the DVI output), and the gnome-display-properties tool properly detected the model, size, resolution... of both screens connected. I would like to know if I can use a command on bash (or a library in python) to get the same information.

The /var/log/Xorg.0.log also shows properly:

(II) intel(0): EDID vendor "NEC", prod id 26345
(II) intel(0): I2C device "HDMIDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "DEL", prod id 41027

I could always parse that file, but it is not the best solution...

I also tried the *ddprobe* command, but for some reason, it only detects one of the screens (the Dell, connected to a DVI cable)

I am currently using Ubuntu 9.04 and Python2.4 (just in case it's relevant)

Thank you very much in advance!

---

### Post by BorrajaX on 2010-07-20
I am going to reply to myself...

The command xrandr seems to work fine and provides me the EDID of the screens

:)

---

