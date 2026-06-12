---
title: "Gamepad Problems"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by spyke01 on 2007-01-16
Hi guys, i just bought a new game-elements wireless game pad, i installed joydev and jscalibrater, i altered my modules file to load joydev and hdci on bootup and ran jscalibrator to test my gamepad. 

All of the buttons work, but i had to calibrate it to get the control pad to pick up all directions. After that i loaded up gxmame to try and get it to work with the pad, i edited the properties to :
> Joystick Type: Standard Joystick
Joystick device prefix: /dev/input/js0

I did the following to verify that the device was working:
```

cat /dev/input/js0

```

I got tons of symbols back so i know its working.

Once inside the game(metal slug 3) i pressed tab and went into the game options, once in there it doesnt pick up any of the gamepad buttons, yet if i play the game it picks up a few. 

Can anyone tell me whats up with the gamepad or tell me where the settings file is so i can manually edit it?

---

### Post by gcranston on 2007-06-24
I have the same problem with an SNES controller rewired to USB.  I've done

```
cat /dev/input/js0
```

and get symbols back on every button, but all the utilities like jstest, jscal, and jscalibrate proclaim that there are only 4 buttons instead of the 8 I should have.  (I'm missing B, Y, Start, and Select).   I don't think joy2key will work if the driver doesn't recognise the 4 missing buttons.

The worst thing is, it used to work just fine under Dapper (I think it was Dapper).  I hadn't pulled it out in a while and was just sitting down for some nice Chronotrigger only to find out that those 4 buttons didn't work.

One last note: obviously, the pad is detected, but here's dmesg:

```
[271299.476000] usb 2-1: new low speed USB device using uhci_hcd and address 5
[271299.648000] usb 2-1: configuration #1 chosen from 1 choice
[271299.676000] input: RetroUSB.com RetroPad as /class/input/input12
[271299.676000] input: USB HID v1.00 Gamepad [RetroUSB.com RetroPad] on usb-0000:00:1d.1-1

```

---

