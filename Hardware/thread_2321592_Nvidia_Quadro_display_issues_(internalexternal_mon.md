---
title: "Nvidia Quadro display issues (internal/external monitor) with 16.04"
date: 2016-04-23
forum: Hardware
---

### Post by eclipticon2 on 2016-04-23
Hi,

I have a Dell Precision mobile workstation with a Nvidia Quadro K1100M graphics card, a docking station and a Dell U3415W (3440x1440) external monitor connected to the docking station via DisplayPort. My new installation of Ubuntu Gnome 16.04 is giving me major troubles with graphics:

* If any of the NVIDIA binary drivers (361.42 or 340.96) is active, output on the external monitor works perfectly and very smooth. If I start the notebook outside the docking station, the internal display switches off when starting the display manager, with no way to get it back alive.

* With the nouveau display driver, the interal display works, albeit the 2D performance is visibly reduced, event the mouse cursor appears jumpy. When docked, the external monitor works, but only the left top part of the screen is being used by the window manager (although the mouse can *jump* around on the whole screen)

* Audio output via DP does not work with any of the drivers (but this is a major issue and already known from Ubuntu 15.10).

Any advice on how to proceed or what tests to carry out?

Thanks!

---

### Post by wooglin280 on 2016-04-25
I am having the same issue. Dell Precision M6800 with Nvidia Quadro K3100M. External monitors connected to docking station work fine. Laptop display is black with a cursor in the upper lefthand corner. Shows dmesg output if i boot with it connected to the docking station. Have you had any luck?

---

### Post by eclipticon2 on 2016-04-25
No, I haven't tried any further and went back to 15.10 (Ubuntu, NOT Ubuntu Gnome, with Nvidia 352.63) as I need to get some work done.

Did not noticed the cursor on the laptop display, though.

What was your previous version that was working still?

---

### Post by wooglin280 on 2016-04-25
I was previously using Ubuntu 15.10. I'm not sure the Nvidia driver version though.

---

### Post by eclipticon2 on 2016-04-25
And you are now also on Ubuntu Gnome 16.04? Or is it the same issue with "original" Ubuntu 16.04?

---

### Post by wooglin280 on 2016-04-25
Same issue with Ubuntu 16.04

---

### Post by wooglin280 on 2016-04-27
I have found a solution that has worked for me. I disabled Nvidia Optimus technology in my system BIOS and now it works as expected.

---

### Post by eclipticon2 on 2016-04-29
Hi and thanks for the update!

When I do the same on my M4800 with the NVIDIA binary driver, the following happens:

Notebook undocked, lid open: Works as expected.
Notebook undocked, lid open, then docked: Works as expected.
Notebook docked, lid closed: **Starts beeping at some stage, upon opening the lid the screen is and remains empty.**
Noteboock docked, lid open: Works as expected.

Any hints on how to further diagnose the problem when the lid is closed?

---

### Post by eclipticon2 on 2016-04-29
One more question - how is your external monitor connected, does sound output work for you?

---

