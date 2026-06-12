---
title: "Keybindings: keyboard function keys to gamepad/joystick"
date: 2009-11-30
forum: Hardware
---

### Post by mstng_67 on 2009-11-30
Greetings!

The problem is simple to explain; hard to troubleshoot, hence the post. I would like to bind keyboard key sequences including the function keys (F1-F12) to button(s) on my gamepad/joystick. The following packages have been installed to support my gamepad:

```
ii  joystick                                   20051019-5ubuntu1                   set of testing and calibration tools for joy
ii  jscalibrator                               1:1.5.6-0ubuntu3                          GTK Joystick Calibrator
ii  libjsw2                                    1:1.5.6-0ubuntu3                          Joystick Library
ii  xserver-xorg-input-joystick                1:1.4.0-0ubuntu1                     X.Org X server -- joystick input driver
```I have used xmodmap -pk to locate the appropriate hex or octal values necessary for placement in xorg.conf. The following is a portion of my xorg.conf file (many lines omitted for brevity):

    ```
##Buttons 1-6 
    Option "MapButton1" "none" 
    Option "MapButton2" "none" 
    Option "MapButton3" "none"
    Option "MapButton4" "key=Alt_L,F4"
    Option "MapButton5" "key=214"
    Option "MapButton6" "none"
    
    ##    Button 7, Left Shoulder.
    #left click is button=1
    #Option "MapButton7" "button=1"

    ##    Button 8, Right Shoulder
    #right click is button=2
    #Option "MapButton8" "button=2"
    Option "MapButton8" "key=0xffe9"
```Here is what I *am* able to accomplish. I can call any single key or key combination from my joystick with the exception of the function keys. The function keys (F1-F12) are, however, precisely the keys I am after. For example, Alt+F4 would be excellent; I could then close any application within Gnome with a single key on my joystick. I can get Alt to work by itself (File menu of any program will fire), but not any function key (or any key combination that includes a function key). I fear there is something special about these keys that is prohibiting my endeavour. Anyone? 

Any and all help is greatly appreciated,

Micheal

EDIT: In case any are wondering, my research on this subject was nearing extensive prior to my post. I have no idea what may be causing this problem which is probably why turning up any answers is proving difficult. I don't mind research; all I need right now is a fresh place to start.

---

