---
title: "USB &quot;RetroPad&quot; hangs using xpad module"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by djhobo9 on 2007-12-19
Hey everyone. I just decided to fire up an NES emulator (mednafen) after a long hiatus. I have two USB RetroPad controllers from RetroUSB.com for the system, and they've both worked beautifully for several years on many other machines.

When I plug one of them in, this shows up at the tail of dmesg:
```
[  349.730762] usb 1-3: new low speed USB device using ohci_hcd and address 2
[  349.944669] usb 1-3: configuration #1 chosen from 1 choice
[  350.023827] usbcore: registered new interface driver xpad
[  350.024135] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  350.062370] usbcore: registered new interface driver hiddev
[  350.072843] input: SealieComputing RetroPad as /class/input/input6
[  350.073147] input: USB HID v1.00 Gamepad [SealieComputing RetroPad] on usb-0000:00:0b.0-3
[  350.073172] usbcore: registered new interface driver usbhid
[  350.073179] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
```

Which is all fine. After doing this and starting mednafen, it works for a few minutes and then becomes "stuck" on one particular button (different one each time). So it'll be like the left D-pad is being pressed infinitely even though it's not. This causes mednafen to hang as the joystick is interrupting and I have to kill the X server. After doing so I can't use the joystick again unless I reboot. Nothing else shows up in dmesg other than what I've already posted.

It did the exact same thing just while being calibrated in jscalibrator and hung that app too, so I know it's the gamepad. I tried both gamepads individually and both have the same problem.

Is there any way to make the gamepad use a different driver or something? This has become extremely annoying and any help would really be appreciated!

---

### Post by djhobo9 on 2007-12-20
bump?

---

