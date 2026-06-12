---
title: "Lots of Problems with Dv7t 3000"
date: 2010-02-05
forum: Hardware
---

### Post by invaderjon on 2010-02-05
Okay well I have been having lots of problems w/ ubuntu karmic on my dv7t 3000 laptop. Here are my problems:

If I close the screen then open it, log off, switch to text view, restart, or switch users then when I try and use my laptop the screen is all fuzzy, it kind of looks like someone put some kind of a tv static texture over my screen. It only goes away if I turn off my laptop then start back up again.

Sometimes when I turn on my laptop the graphics flicker off but then don't turn back on (blank screen, screen IS off)

Sometimes when I start up my laptop the mouse doesn't turn on and I have to turn off the computer and turn it back on. 

I cannot for the life of me get Fallout 3 to run on my laptop, but I can run it on my desktop.

*note: I am running linux off an external 1.5 tb harddrive

I do not get ANY of these problems when I boot linux on my desktop computer only when I run it on my Dv7t 3000 Laptop.

---

### Post by agnes on 2010-02-05
What's your graphics card? Do you have the correct driver installed?
Because, it appears it has to do with that last thing.
If so..

If you don't know your card for sure run **sudo lshw | less** and search for **-display*, look what's under *product*. Find linux driver for it online.

Also, have you tried System->Administration->Harware Drivers yet?
Another method for obtaining the right driver is using the program EnvyNG.

---

