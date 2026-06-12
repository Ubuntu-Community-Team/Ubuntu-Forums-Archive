---
title: "Saitek PS2700 gamepad: set-up issues"
date: 2011-04-09
forum: Hardware
---

### Post by Logseman on 2011-04-09
Greetings!

I'm Logseman, I've been using Ubuntu for a year or so and I'm quite happy with it. At the moment I run Ubuntu 10.10 in a Toshiba Satellite computer.

However, I come here for a quite specific matter. I have a Saitek PS2700, a gamepad which resembles the PS2 controller but with the little bonus of being able to swap the left-hand joystick and D-Pad.Here you have the thing: 
[IMG]http://di1-2.shoppingshadow.com/images/pi/55/6c/b0/90364308-260x260-0-0_Saitek+PP32+PS2700+Rumble+Pad+for+PC+or+PS3.jpg[/IMG]

At any rate, the issue is the following. The gamepad is recognised, I get the following output when typing "lsusb":
```
Bus 006 Device 002: ID 06a3:f620 Saitek PLC
```
I've installed the "joystick" package as well.
Nevertheless, I don't quite figure how to connect it with joy2key. When I run ```
joy2key -terminal
``` it seems not to heed my commands. Regardless of the buttons I push, I get stuck in the first axis calibration:
```
Calibrating axis 0
Please center the axis and press a button.
```

While searching for similar issues, I've noticed as well that many of the links referring to the issue are very old, so I don't know if it's because noone has this kind of issues or because they never got solved...

Thanks in advance! ;)

---

