---
title: "TIP: How to get your MS Intellimouse working correctly."
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by Joshatdot on 2006-01-15
Edit your xorg.conf file with this to get your Wheel, Wheel Click, Back and Forward buttons to work like they should!

```
Section "InputDevice"

   Identifier  "Mouse1"
   Driver      "mouse"
   Option      "Protocol"     "ExplorerPS/2"
   Option      "Device"       "/dev/input/mice"
   Option      "Buttons"      "7"
   Option      "ZAxisMapping" "4 5"

EndSection
```

---

### Post by Sef on 2006-01-16
How do you get into the xorg.conf file?

---

### Post by Name on 2006-01-26
[QUOTE=Sef]How do you get into the xorg.conf file?[/QUOTE]

open terminal and type sudo gedit /etc/X11/xorg.conf

its case sensitive...

---

### Post by Ocxic on 2006-01-26
i have the mouse in question and it worked perfectly for me right from the get-go.  MS usb intellimouse

---

### Post by outofnicks on 2006-03-29
Can I have double-click action with a single click of the scroll wheel, and how?
I have the intellimouse on my Dell--on my Mac an iOptiJr mouse has this feature. Not familiar with PC, so don't know if it should be expected.

---

### Post by Joshatdot on 2006-05-19
[QUOTE=Ocxic]i have the mouse in question and it worked perfectly for me right from the get-go.  MS usb intellimouse[/QUOTE]
I had my MS Intili connected via PS2, cause all my USB ports were taken.  I bet if I had it in a USB port it would work from the get-go.

[QUOTE=outofnicks]Can I have double-click action with a single click of the scroll wheel, and how?
I have the intellimouse on my Dell--on my Mac an iOptiJr mouse has this feature. Not familiar with PC, so don't know if it should be expected.[/QUOTE]
That I am not sure ... but there has to be away to remap the mouse buttons in Gnome.

---

### Post by Joshatdot on 2006-06-08
It was the **xev** command, it reads input from the Mouse and displays their clicks, mappings, buttons.  

You run the command from a xterm, and displays a new window with a little box you click around in, and it dumps the input to the xterm.

---

