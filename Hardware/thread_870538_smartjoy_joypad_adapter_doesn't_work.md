---
title: "smartjoy joypad adapter doesn't work"
date: 2008-07-25
forum: Hardware
---

### Post by ambyra on 2008-07-25
I installed the joypad drivers and got my logitech dual action pad to work, but the smartjoy ps1 to usb adapter doesnt (as I anticipated). Is there anything I can do?
When I jscalibrate the computer doesn't detect anything, and the signal indicator doesn't show any input.

I did a sudo chmod 666 /dev/input/js1 and now my js0 logitech controller controls js0 and js1. My smartjoy ps1 doesn't do anything. I tried a sudo chmod 666 /dev/input/js2 but now the logitech controls all three.

---

