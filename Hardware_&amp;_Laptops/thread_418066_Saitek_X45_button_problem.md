---
title: "Saitek X45 button problem"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by teutori on 2007-04-22
With Edgy (kernel 2.6.17-11) I had no problems with my Saitek X45 -joystick but now when I updated to Feisty (kernel 2.6.20-15) the buttons on the stick are messed up.

Jstest shows that it has only 16 buttons and it should have at least 26 buttons. All axis work as they should. Some of the buttons flicker constantly if I move some axis when I checked them with Kubuntu's joystick calibrator and some buttons don't work at all.

$jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (Saitek Saitek X45) has 8 axes (X, Y, Rx, Rz, Throttle, Rudder, Hat0X, Hat0Y)
and 16 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC).
Testing ... (interrupt to exit)

$ dmesg | grep Saitek
[   34.293660]  hdb:<6>input: Saitek Saitek X45 as /class/input/input2
[   34.300771] input: USB HID v1.00 Joystick [Saitek Saitek X45] on usb-0000:00:02.0-1.3

---

### Post by teutori on 2007-04-22
I just realized that because the joystick is detected with 16 buttons button number 17 overlaps with button 1, 18 overlaps with 2 and so on. When I test it with jstest if I press button 1 it's state flickers on and off; if I press button 17 then the state of button 1 flickers on and off too; if I press buttons 1 and 17 together the state for button 1 stays on.

Does anyone have a joystick with more than 16 buttons working with Feisty?

---

### Post by womail on 2007-05-11
I have an X52, same problem, 16 buttons are recognised rendering a lot of other buttons useless. Very odd, I use Suse 10.2 also and there is no problem whatsoever.

---

### Post by Saubazi on 2007-05-12
Same problem - feisty's kernel joystick driver is shafted. I don't know if it's general in 2.6.20 or ubuntu specific - I think it is general - should be fixed on next release. When that one is out - dunno...I downgraded to Edgy myself everything works fine again.

---

