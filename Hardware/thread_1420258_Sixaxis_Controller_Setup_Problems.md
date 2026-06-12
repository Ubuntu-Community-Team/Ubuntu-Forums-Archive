---
title: "Sixaxis Controller Setup Problems"
date: 2010-03-02
forum: Hardware
---

### Post by notamuppet on 2010-03-02
I'm using Ubuntu 9.10 and I cannot get my sixaxis controller to work as a usb controller for zsnes.

When I try to manually the set up the controller it constantly inputs "J19" as a command.  If I click the arrow keys fast enough I can get the actual command (J14,J16,etc.) to input but none of the others.  I think the problem has to do with the fact that the led's are constantly flashing and inputting a command.

I have manually set up the controller on an older distro about a year ago with no problems.

---

### Post by notamuppet on 2010-03-03
I also tried this guide ([https://help.ubuntu.com/community/Sixaxis#Using](https://help.ubuntu.com/community/Sixaxis#Using) the Sixaxis as a Pointer Device ) but I couldnt get it to work

---

### Post by notamuppet on 2010-03-06
bump

---

### Post by fdm on 2010-06-23
I had the same issue with a sixaxis controller with lucid. The main problem as far as I could tell is that buttons are axises too, so when you press one button you are pressing three. I resolved it as much as I could using QTSixA to set the controls to keyboard keys and using the keyboard to configure the apps. From there I can just plug in the controller and push the button in the middle and everything works.

---

