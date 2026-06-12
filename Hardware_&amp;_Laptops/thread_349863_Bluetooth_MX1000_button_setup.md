---
title: "Bluetooth MX1000 button setup"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by gearshifter on 2007-01-30
Does anyone know how all the settings work to get all the buttons on my bluetooth mx1000 to work.  I tried the regular mx1000 Howto and get an xorg failed to launch screen. 

I have tried numerous things but i have no idea what to do.

---

### Post by ice_dm on 2008-01-18
I don't have every button working but I got the ones I use most.
I followed [http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)
I was able to get back, forward, scrolling buttons and scrolling wheel. 

In my /etc/X11/xorg.conf I left most everything the same.
In the  InputDevice Configured Mouse section I made 4 line changes

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option	   "Buttons" "12"
    Option         "Emulate3Buttons" "false"
EndSection
```

The only changes are these lines

```
   
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option	   "Buttons" "12"
    Option         "Emulate3Buttons" "false"

```

---

### Post by revoltism on 2008-01-20
Thanks alot pal.. now i can rotate the cube by changing the settings in Compiz to button9 (forward button)

---

