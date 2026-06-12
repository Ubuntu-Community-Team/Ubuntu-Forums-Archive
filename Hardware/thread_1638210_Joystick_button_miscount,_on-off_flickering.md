---
title: "Joystick button miscount, on-off flickering"
date: 2010-12-05
forum: Hardware
---

### Post by paulscode on 2010-12-05
Hello, I am running Ubuntu Lucid 64-bit, and I'm trying to get my Nintendo 64 controller and USB converter to function.  It works properly in Windows XP, so I know it is not a problem with the hardware itself.

When the device is plugged in, it shows up as /dev/input/js0.  From the terminal, running jscal gives me the following:
```
paul@ASUS:/dev/input$ jscal /dev/input/js0
Joystick has 4 axes and 16 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 2 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 3 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751

```

First off, this information is incorrect - the number of buttons is wrong.  It should be 4 axis and 10 buttons, not 4 axis and 16 buttons.

Then when I run jstest, three or four of the "16" buttons flicker rapidly between on and off.  Pressing some of the buttons on the actual joystick works, while other buttons do not.

Has anyone had a similar problem and found a good solution?  I hate having to reboot into Windows XP every time I want to play some of my games.

---

