---
title: "Proper WiiCan Mappings for Classic Controller Pro"
date: 2015-09-15
forum: Hardware
---

### Post by rte613 on 2015-09-15
Put simply, the mappings around the internet that users are told to use for gaming with a Classic Controller Pro *_**DON'T WORK.**_* The DPad will end up mapped to left joystick values, left joystick will be vertically inverted, and input will not function for either joystick. Frankly, what was one of the best designed controllers ever becomes an unusable mess. Again, DO NOT USE MAPPINGS FOUND AROUND THE INTERNET FOR THIS CONTROLLER.

If, however, like me you enjoy your Classic Controller Pro enough to put some work into fixing it, we can make WiiCan mappings for any emulator, or even as a pointer, relatively easily.

1. First, open WiiCan, and double click on "Classic Controller" to edit the mappings.

2. Replace ***"Classic.DPad.X = ABS_X"*** with ***"Classic.Up = BTN_FORWARD"***, and under that, make another mapping ***"Classic.Down = BTN_BACK"***.

3. repeat step 2, with ***"Classic.DPad.Y = ABS_Y"***, but instead, replace it with ***"Classic.Left = BTN_LEFT"*** and ***"Classic.Right = BTN_RIGHT"*** under that.

4. Replace ***"Classic.LStick.X = ABS_HAT0X"*** with ***"Classic.LStick.X = ABS_X"***.

5. Repeat step 4, substituting Y for X in both lines.

6. Replace ***"Classic.RStick.X = ABS_HAT1X"*** with ***"Classic.RStick.Y = ABS_RX"***.

7. Repeat Step 6, again substituting Y for X

8. Disconnect controller, restart WiiCan, and Reconnect.

YOU'RE DONE, you should now be able to use all buttons and axis with whatever program you please! :D

---

