---
title: "Sixaxis PS3 controller paired but no input from it"
date: 2013-01-15
forum: Hardware
---

### Post by cphus on 2013-01-15
Hello Ubuntu,

I got from eBay a (I presume a copy) of a PS3 controller for like 10$.
I tried it in Windows to see it it's not just a bunch of plastic that looks like a PS3 controller and it worked. 

In Linux (Kubuntu 12.10, kernel 3.5.0-21) howver I can't seem to make it work. What does work: 

$ dmesg | grep sony
```
[ 3939.473853] sony 0003:054C:0268.0009: Fixing up Sony Sixaxis report descriptor
[ 3939.476008] sony 0003:054C:0268.0009: input,hiddev0,hidraw1: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.0-1.2/input0

```$ lsusb | grep Sony
```
Bus 002 Device 013: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
```

Now, I have QtSixA (1.5.1) and I successfully pair the device with the in-menu option. Then I select a profile, for key assignments, like Neverball; I open Neverball and nothing works. 

What I also did is try to get it work via bluetooth from terminal. After I pair with 'sudo sixpair' I disconnect the usb cable and start sixad. I get the message to press the PS3 button. Of course, I press the button but at this point it hangs and waits. 

Also, when I connect it via USB, under /dev/input I get a js0 entry. I do a jstest on that js0 and I get full of info like 
```
Joystick (Gasia Co.,Ltd PS(R) Gamepad) has 27 axes (X, Y, Z, Rz, (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null))
and 19 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC, (null), (null), (null)).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:o
```The Axes thing repeats many more times furthemore. but I cut it.

Any ideas, suggestions?

---

