---
title: "Homebrew: Touch screen with stylus/pen (Similar to Wacom)"
date: 2009-10-28
forum: Hardware
---

### Post by jhoe on 2009-10-28
[SIZE="1"](Sorry admins if this isn't in the correct forum.)[/SIZE]

[FONT="Verdana"]Hello.

My goal is to take a LCD I own and turn it into a touch screen.  This screen will also support use with a stylus/pen that can be used as a mouse.  Basically a homemade Wacom Cintiq.

I already have the LCD in hand and the capacitive touch screen picked out.  The problem I am finding is that no pen exists, that will work with a capacitive screen, that has buttons (to be used as a mouse).

The requirements for the stylus/pen is that it must have at least two buttons, i.e. right and left click, and work with a capacitive screen.  I was looking at Wacom pens but their pens connect to the digitizer instead of the computer via Bluetooth.

Do you know of a stylus/pen with 2+ buttons that I am not finding?

The only thing I can think of right now is getting a Wacom stylus, modifying it to work with a capacitive screen and simply not use the Wacom tablet.  In other words, buy a cheap Wacom only to be the middle man (for mouse clicks) between the stylus and the computer.

Any ideas that I could try?  I have a fair knowledge of circuits so building something to make this work is not out of the question.

I have seen others take a Wacom digitizer and place it behind their LCD but this would require a large (expensive) Wacom tablet to be taken apart.

Any help or suggestion will be much appreciated.[/FONT]

---

### Post by Sef on 2009-10-29
1) Moved to Hardware and Laptops.

2) What version of Ubuntu are you planning to use on it?

---

### Post by jhoe on 2009-10-29
> **Sef said:**
> 1) Moved to Hardware and Laptops.

Thanks.

> **Sef said:**
> 
2) What version of Ubuntu are you planning to use on it?

9.10 most likely.  Saving a few more pennies before I grab a 4 port SAS RAID controller (leaves some space to add drives, I don't think I'll use more than 250 drives :) ). So the OS isn't installed yet. 

I am trying to find out if any Wacom pens will sync with a computer or only the board itself.  All I really need is a stylus/pen that performs mouse clicks.

---

### Post by Tordre on 2009-12-15
I don't think you fully understand how the stylus works for wacom, I don't fully understand it myself, but it appears to be a series of wire traces under the board, which gives off and pick up a small em field from the pen itself (I am thinking in a way much similar to how RFID works, I say this because the pen has tripped the RFID security sensor at my university's library before), allowing it to detect placement. Also based on changes in the field, other things can be determined, such as pressure, mouse clicks, and weather or not you are using the tip or the eraser. 

The only way I can think of is if you do something like put a wacom board under the screen, and a capacitive screen on top, you might need to do some fancy fiddling so that when the wacom detect the mouse click it disables the input from the touch screen or else everything might become a double click. 

If you don't mind could you post the source for the touch screen, I am thinking of using one in a project I am considering.

---

