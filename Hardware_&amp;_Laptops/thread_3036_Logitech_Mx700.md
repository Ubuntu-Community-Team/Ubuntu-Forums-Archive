---
title: "Logitech Mx700"
date: 2004-11-02
forum: Hardware &amp; Laptops
---

### Post by AlePetrucci on 2004-11-02
Hi all
a simple question....
is there a way to use alle 7 buttons ofmy logitech mx700 (cordless with 7 buttons)? 
i mean, the buttons are ok...but i'd like to set the 2 buttons on the left (the 2 arrow) to go back and forward in firefox and nautlus....as under M$ windows.... now the "go back" button is for cut&paste and the "go fwd" button act as the normal right button...
i hope u understood what i mean...sry but my english isnt so good  =P~

---

### Post by dave_blob on 2004-11-02
Hey i got my mx700 to work quite well.
Followed the step by step instructions here:

[http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46)

A few things to note: 
Dont worry about all that checking for evdev and patching and all that, i know for a fact it works in the current Ubuntu kernel. So you can skip step 1.

Also, when he says:
Option        "Dev Name" "Logitech USB-PS/2 Optical Mouse" # cat /proc/bus/input/devices
        Option        "Dev Phys" "usb-*/input0" # cat /proc/bus/input/devices

it means you have to run the cat command in the comment, and change the dev Phys and Name to the value returned by it. Hard to explain, but just run the command, it'll make sense.

Finally, if you just want the side buttons, you can skip step 4. The current Ubuntu is set up to automatically recognise the side buttons as back and forward, at least in firefox anyway.

Good luck!

---

### Post by stresscrash on 2004-11-02
i keep getting a cannot open device error upon X startup

---

### Post by dave_blob on 2004-11-07
[QUOTE=stresscrash]i keep getting a cannot open device error upon X startup[/QUOTE]
 You must make sure you have set the dev phys to the right value.
Post the relevent section of your XF86config (the bit with the mouse setup) and also the output of 
cat /proc/bus/input/devices

please

---

