---
title: "pointer sticks on right monitor, Wacom USB Intuos4 on ubuntu 10.10"
date: 2011-04-03
forum: Hardware
---

### Post by subdolo on 2011-04-03
Hi, i tried to install a wacom usb intuos4 tablet on my system.

Current buggy behaviour:

- the tablet is able to move the pointer
- when the pointer is on my left screen i'm able to move it to the right edge of the monitor (the tablet maps the first screen).
- as i reach the right edge of the left screen the pointer jumps to the right edge of the right screen.
-as the pointer is on the right screen the table maps the whole and only right screen, no way to bring it back to the left unless the mouse is used.

The behaviour i'd like to have:

- absolute pointer positioning scheme, spanning through the two monitors (left part of the table mapped to left screen and right part mapped to right screen)

Current configuration:

-Wacom intuos4 usb tablet.
-two monitors with different resolution (the main one:1680x1050 to the left, and a smaller 1280x1024 to the right).Configured as separate x screens.
-nvidia graphic card (GeForce9600GT), with nvidia drivers installed (260.19.06)


I read of people having similar issues, though i never found any clear answer.

i imagine  some config files should be posted as well but not being too familiar with them i  wait to read which are needed.


thanks to everybody

---

### Post by Favux on 2011-04-03
Hi subdolo,

Welcome to Ubuntu forums!

> -two monitors with different resolution (the main one:1680x1050 to the left, and a smaller 1280x1024 to the right).Configured as separate x screens.
I think right now it is behaving as it is suppose to but now how you want it to.  I think you want to turn the two monitors into one Desktop by using the Nvidia X Server Settings applet to convert the two separate screens into a TwinView type setup.  That should do what you want.  If you visualize mapping the two monitors onto your tablet you'll see you will lose a little rectangle on the bottom right side of your tablet.

The changes should show up in your xorg.conf in /etc/X11.  The Nvidia applet should make a backup (and probably already has made one since it was installed and presumably has already changed your xorg.conf) but you might want to do one first from your current working xorg.conf.  So you can restore it from the command line if something goes wrong.

---

### Post by subdolo on 2011-04-03
Yes! that perfectly sorted the problem out!

simply changing the setting from x screens to twin view perfectly solved the problem 

Thank you so much, i owe you one! ;)



Subdolo

---

