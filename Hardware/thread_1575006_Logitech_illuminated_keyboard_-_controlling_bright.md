---
title: "Logitech illuminated keyboard - controlling brightness via command line"
date: 2010-09-15
forum: Hardware
---

### Post by zsugiart on 2010-09-15
All, 

Sorry if this is not in the right category, pls move it as appropriate. I have been scouring the threads and I believe this hasn't been asked before. 

I've got myself a Logitech Illuminated keyboard, it's backlight can be controlled from a button in the top-right of the keyboard. 

I am trying to find ways to trigger the brightness change via the command line ( or any programmatic means to control the backlight in Ubuntu )

The purpose is simple: I want the backlight to turn ON when I am not idle, and to turn OFF when I am idle. I don't see the point of the backlight staying on when I am not in front of my computer.  

Any idea where I can start digging?

Cheers,
Z

---

### Post by zsugiart on 2010-09-15
Reading [https://wiki.ubuntu.com/Hotkeys/Architecture](https://wiki.ubuntu.com/Hotkeys/Architecture) just now and tried using showkey from a console.

It seems that the top right key of this keyboard does not register any key event whatsoever, dmesg also didn't show any activity

My knowledge is limited but this seems to me to indicate that the light control is completely independent of the OS. The question is then is there a way to send some kind of signal/event from the OS to the keyboard to control the backlight?

---

### Post by Grenage on 2010-09-15
Having not used that keyboard, nor knowing how it functions internally...


I imagine that the control is indeed completely independent, being a manual control for the lights.  I can't see how you would be able to control the light without modifying the hardware.

---

