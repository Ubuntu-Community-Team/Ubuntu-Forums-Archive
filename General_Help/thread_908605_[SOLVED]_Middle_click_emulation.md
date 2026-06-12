---
title: "[SOLVED] Middle click emulation?"
date: 2008-09-02
forum: General Help
---

### Post by mdecler2 on 2008-09-02
Could you help me get middle click emulation working in Ubuntu Hardy?
I used to call it "middle click emulation." It involves pressing both left and right mouse buttons for certain copy/paste functions.
I upgraded from Dapper to Hardy recently by doing a fresh install, and I noticed that I can no longer do middle click.

I tried some searches on Google and found very little to nothing useful for my situation...they were mostly about Macs. I have a Dell 8400 PC and MS mouse.

---

### Post by Shazaam on 2008-09-02
Just a guess-
Look in /etc/X11/xorg.conf, see if this is there (under "Input Device" "Configured Mouse")...
```
Option         "Emulate3Buttons" "true"
```

---

### Post by baggins on 2008-09-02
Somewhere in /etc/X11/xorg.conf you should find a section something like this
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```
My mouse have a scroolwheel thats what the ZAxisMapping line is for and ofcourse the "Protocol" line will depend on your mouse.
What you are seeking is the Emulate3Buttons bit.
Edit the mouse section to include Option         "Emulate3Buttons" "true" 
log out ... login again and it should work (Does for me anyway :) )

-- Jon

---

