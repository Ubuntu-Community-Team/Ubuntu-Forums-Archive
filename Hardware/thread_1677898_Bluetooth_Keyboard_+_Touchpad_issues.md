---
title: "Bluetooth Keyboard + Touchpad issues"
date: 2011-01-29
forum: Hardware
---

### Post by justiceeeeeeeeeeeeE on 2011-01-29
I am using Ubuntu 10.10 64 Bit. I am trying to get my bluetooth keyboard/touchpad to work. As it stands right now the bluetooth manager can see the keyboard/touchpad. I can get as far as entering the pin it gives me. Once I enter the pin on the keyboard and press enter the keyboard is no longer responsive.

If I use this command in the terminal:
 sudo hidd --server -t 2 --connect (macaddress for keyboard) 

Then the keyboard works (for some reason I have to enter this command twice). However if the keyboard sits for a few minutes it seems to disconnect and the process has to be started over again. Anyone have any ideas?

---

### Post by splash_ on 2011-01-31
Hey man.

This issue was solved here: [http://ubuntuforums.org/showthread.php?t=1647637&highlight=pin+bluetooth&page=1](http://ubuntuforums.org/showthread.php?t=1647637&highlight=pin+bluetooth&page=1)

In a nutshell: you need to upgrade your bluez package. 

I wrote about it here: [http://mylabsk.blogspot.com/2011/01/non-persistent-bluetooth-pin-code-with.html](http://mylabsk.blogspot.com/2011/01/non-persistent-bluetooth-pin-code-with.html)

Good luck!

---

