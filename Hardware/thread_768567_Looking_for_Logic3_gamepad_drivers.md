---
title: "Looking for Logic3 gamepad drivers"
date: 2008-04-26
forum: Hardware
---

### Post by Chronotrigger_BG on 2008-04-26
Hello
I am trying to use my new gamepad with ubuntu and there are some difficulties. When I run jscalibrator, it shows that the gamepad has 30 axes and 12 buttons. Now, the 30 axes are allright, it's a PS3/PC pad and most of the buttons are 0-255.

The problem is that the current driver only finds twelve buttons and there are actually fifteen. Out of the four "important" buttons, only the triangle button works.

I repeat - All the things that should be there are there. When I push the buttons, their corresponding axes move. But There are only 12 slots for 15 buttons.

What I want to know is this - how do I set the remaining few buttons? I need a program or at least the name of the file that needs to be edited.

Here are some specifics:

The gamepad is Logic3 Stealth
Its model is PS903X

lsmod | grep 'game\|joy' :

gameport               16776  1 analog
joydev                 11328  0 

By the way, some of the axes seem to be redundant. Is this an unused feature, or does my gamepad have some other means of control that I don't know about(motion-sensing?)?

Thanks in advance :)

---

### Post by Kelderkeuken on 2008-10-12
I have this exact same issue with a Logic3 'Freebird Stealth Pad' PS907. It's a ps3 controller clone. When using *jscalibrator* you can see that pressing the square, circle and cross buttons are registered as axis, but they are not mapped to a button. There are only 12(13) buttons where there probably should be 15(16) (there is a button 0). It actually displays too many axises (30) yet not enough buttons. I have tried a lot of different ways to get it to work but to no avail as of yet. If anyone could help with this that would be great.

vendorID 0x054c
productID 0x0268

---

