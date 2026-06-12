---
title: "logitech g7 mouse help"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by Wezley on 2007-06-13
hi, im new to ubuntu/linux, and im having trouble getting my mouse to fully work.  i have a logitech g7 wireless mouse, and it functions basically ok,  but to be honest, i need the back button to work (ie. go back in a page in firefox, or the file browser)....ive just gotten so used to it.  i tried looking around and editing the xorg.conf file, but that ended up messing up my x window system completely and i had to do another install of ubuntu.  is there a good way to  make the buttons work on this mouse in linux?  

thanks, wes.

---

### Post by Vonagio on 2007-06-19
I have the G7 mouse and have the back button working correctly in Firefox, but not in file browser (that doesn't bother me that much). The mouse settings in xorg.conf are
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "6"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6"
EndSection
```

This works for me ok, button 1 is left click, 2 is right click, 3 is scroll clicked down, 4 is scroll forward (up), 5 is scroll back (down), and 6 is the back button.

I have not figured out how to use button6 as back in File Browser, and I have not been able to use the left and right scroll either (but i don't use those in XP as i don't like having the extra software (logitech setpoint) running for such a small feature).

Hope this helps,

Von

EDIT: You'll have to restart the xserver for changes to take effect: Control + Alt + Backspace (save everything you have open before doing this), or Restart.

---

