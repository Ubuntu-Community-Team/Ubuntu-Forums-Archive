---
title: "SIXAXIS as keyboard and mouse"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by jaime77 on 2008-01-11
I have found a post that say how to configure a mouse to send keyboard events (like crt+f4, alt+g, etc) but say just work for mouse and butons, no combinations that is what i want.
Another post say how to map a button from the joypad to a key, but its very basic, and no mention of combination, and it requieres initiate for each window, i want it to be default to the full system, like keyboard and mouse.

What i want (i dont know if it is even posible) is use the SIXAXIS (playstation 3 joypad) as a full replacement from a mouse and keyboard.

Let me try to explain (if you have played killzone you must understand what i want more easy)

For the keyboard, its a combination of the analog stick and the 4 main buttons in the right, imagine 9 squares in the form of a phone keypad, each one with 4 keys (a,b,c,shift,alt,etc), that give us 36 keys, enough for a basic keyboard, now to use a particular key, you move the analog stick to one side (this way selecting one of the 9 squares) and click one of the 4 buttons to select one of the 4 keys in that square.

For the mouse, use the analog stick to move around the cursor, left and right click from the mouse mapped to some button in the joypad.

I really want this, so if its not posible yet, with any program or configuration available today, i will try my best for make it posible, just dont want to create something if it is already made.

Any help, orientation, tips, useful guides, its really apreciated, since i will star from zero, because i never have made drivers before (i guess it is what i need) or programs, or anything.

---

### Post by Holmen on 2008-03-03
Yes, this is possible, due to the ```
xserver-xorg-input-joystick
```.

Connect your SixAxis control to your Ubuntu-computer - [http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html)

Install the input-joystick package from the repo and configure it as you wish.

Read the manual for it - ```
man joystick
``` from a terminal.

Restart X and youre done!

---

