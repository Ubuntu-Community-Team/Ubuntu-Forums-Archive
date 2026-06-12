---
title: "HP Paviliondm3 touchpad on/off button"
date: 2010-02-17
forum: Hardware
---

### Post by sventek on 2010-02-17
Hi,
any help or suggestions here is greatly appreciated.
I have this laptop HP and the touchpad has an on/off button, but I cant seem to
find the Linux driver for this on/off switch.  Anyone have any suggestions//ideas
please? Thanks.

---

### Post by sventek on 2010-02-17
Solved:

Didn't find the driver for the Mousepad button but I did find a .sh script
that if you save the script in /Usr/Bin and make sure it is set as executable, 
then it will turn the mousepad on and off.

Next just open "Keyboard Shortcuts" from System/Preferences and type the path
to the Mousepad.sh script.
Next press the touchpad on/off button after pressing the shaded area in the 
input box.  This assigns the script executable to the button.
Voila.
#!/bin/bash

if [ -e /tmp/mouse-disabled ]; then
  rm -f /tmp/mouse-disabled
  xinput set-int-prop 'ImPS/2 Generic Wheel Mouse' 'Device Enabled' 8 1
else
  touch /tmp/mouse-disabled
  xinput set-int-prop 'ImPS/2 Generic Wheel Mouse' 'Device Enabled' 8 0
fi; 
Oh, and here the .sh script:

---

### Post by sventek on 2010-05-01
ok ..me here again..I've since then upgraded to Lucid 10.04 and the same script doesn't seem to work now..are the paths correct?

---

