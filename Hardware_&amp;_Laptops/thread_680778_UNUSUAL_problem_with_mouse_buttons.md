---
title: "UNUSUAL problem with mouse buttons"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Thasat on 2008-01-28
Hi

I've been using Mint Cassandra (it's based on Ubuntu) for about 7 months but decided to install Xubuntu yesterday due to long delays of XFCE edition of new Mint Daryna.
The desktop enviroment being used is not important because i think the problem is related directly to xorg.
I encountered very strange (in my opinion) problem with mouse buttons. Two of them didn't work out of the box as I wanted them to but there is nothing strange with it. I just run xev to check how buttons were mapped and got this:
Left mouse button: button 1
Wheel: button 2
Right mouse button: button 3
Wheel up: button 4
Wheel down: button 5
Side button 1: button 2     <===!
Side button 2: button 3     <===!
I want them to be mapped as button 6 and 7.
First thing i tried is adding 
Option "Buttons" "7"
to my xorg.conf and this is where things start to get strange. When I restart gdm i'm getting "Ubuntu is running in low-graphics mode". How is mouse related to graphics? Commenting out the buttons option in xorg reverts things back to normal.
My second attempt was with evdev (that worked on Mint), just standard configuration from the evdev manual:
Section "InputDevice"
         Identifier "mouse"
         Driver "evdev"
         Option "evBits"  "+1-2"
         Option "keyBits" "~272-287"
         Option "relBits" "~0-2 ~6 ~8"
         Option "Pass"    "3"
Same result. I also tried other evdev configuration as proposed in some guides here on forums but the still make my xorg run in low graphics mode.

My xorg.conf is default, I didn't change anything in it except the mouse section.

Thanks in advance

---

### Post by Pandemic187 on 2008-01-28
I'm not sure I can help you, but what sort of mouse are you using?

---

### Post by Thasat on 2008-01-28
I'm using A4tech mouse:
[IMG]http://www.a4tech.pl/Pictures/A4T/MYS/09019/avre_09019b.jpg[/IMG]
Connected to USB, it has 7 buttons (not counting wheelup and wheeldown).

---

