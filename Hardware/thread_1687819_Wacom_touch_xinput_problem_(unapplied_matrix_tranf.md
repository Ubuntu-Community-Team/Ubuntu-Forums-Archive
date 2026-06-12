---
title: "Wacom touch xinput problem (unapplied matrix tranformation)"
date: 2011-02-14
forum: Hardware
---

### Post by Trooper_Max on 2011-02-14
So I've been fiddling with xinput to try to make use of both touchscreens on the Toshiba Libretto w105 dual-screen umpc. Everything works fine when using only one screen or if the screens are mirroring each other. But once you try to separate the screens, the touch inputs no longer map correctly to the screens.

I figured out how to almost correct this using the xinput command (see quote below), but for some reason, the "press" event isn't getting transformed by the matrix like the motion and release events are. I'm hoping someone with more experience with wacom pads or touch/pen inputs may know something about this or be able to offer some advice on getting this resolved.

> **Trooper_Max said:**
> Almost got it figured out. Running Kubuntu  alpha2, I set the second monitor to be positioned below the first. This  of course messed up the touchscreen coordinates, so I went to the  terminal to fix it. Here's the process I went through:

***"xinput list"*** shows the touch devices as "Wacom ISDv4 E2 Finger touch" with id's 12 and 13.

***"xinput list-props 12"*** shows the properties for the first touchscreen.
[I]
**"xinput set-prop 12 125 0"**[/I] sets the Device Enabled property for the first touchscreen to 0 (off)
***"xinput set-prop 13 125 0"*** sets the Device Enabled property for the second touchscreen to 0 (off)

***"xinput set-prop 12 125 1"*** to re-enable the first  touchscreen and verified by tapping on the top screen that it is indeed  the first screen. Noticed that the x coordinate is correct, but the y  coordinate is twice what it should be.

***"xinput set-prop 12 127 1, 0, 0, 0, 0.5, 0, 0, 0, 1"*** sets the transformation matrix to scale the y coordinate by half. Doing this almost corrects it.

***"xinput test 12"*** puts the terminal in a loop and outputs  the events... [SIZE=2][COLOR=Red]**when I tap the top screen, it triggers a motion event at  the correct coordinates, followed by a button press at the  untransformed/incorrect coordinates just as if the matrix hadn't been  applied, followed by a button release at the correct coordinates.**[/COLOR][/SIZE]

***"xinput set-prop 13 125 1" ***re-enables the second touchscreen.
***"xinput set-prop 13 127 -1, 0, 1, 0, -0.5, 1, 0, 0, 1"*** similarly almost fixes the second screen, but it has the same problem.

For reference, ***"xinput set-prop [device] 127 A, B, C, D, E, F, G, H, I"*** corresponds to the matrix:
[FONT=Courier New][A][D][G]
[B][E][H]
[C][F][I][/FONT]

**Cheatsheet for transformations:**
A = X scale
B = X skew
C = X offset

D = Y skew
E = Y scale
F = Y offset

G=H=0
I=1

This is a pretty good reference too, but there are plenty of others:
[http://www.senocular.com/flash/tutorials/transformmatrix/](http://www.senocular.com/flash/tutorials/transformmatrix/)

Probably easier to just base it off the code above though.

**So if we could just figure out why the press event isn't getting transformed, we'd be set.**

I'm starting to look at the "xsetwacom" command, but haven't figured out if it can help here yet...

Thanks in advance for any advice!

 ~Troop

---

### Post by Trooper_Max on 2011-02-17
In case it helps any:

```

troopermax@Libby:~$ dmesg | grep wacom
[    9.382569] usbcore: registered new interface driver wacom
[    9.382574] wacom: v1.52:USB Wacom tablet driver

```

Let me know if more info is needed!

~Troop

---

