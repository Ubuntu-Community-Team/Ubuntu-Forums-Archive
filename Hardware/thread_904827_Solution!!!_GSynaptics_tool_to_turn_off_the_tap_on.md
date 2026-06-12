---
title: "Solution!!! GSynaptics tool to turn off the tap on my Touchpad."
date: 2008-08-29
forum: Hardware
---

### Post by brigadoon on 2008-08-29
I was tired of the touchpad on my Toshiba Satellite interfering with my poor typing skills. I am running Ubuntu 8.04 and loving it. I'd be typing away when *BAM!* the keyboard cursor jumps to a different line because I touched the touchpad. I downloaded and installed GSynaptics to turn off the tap option on my touchpad. It didn't work because my xorg.conf file was missing some lines. I made the following changes to the xorg.conf file...

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Synaptics Touchpad" "AlwaysCore" [COLOR="Red"]Added this line[/COLOR]
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "synaptics" [COLOR="Red"]Added this line[/COLOR]
EndSection

Section "InputDevice" [COLOR="Red"]Added this line[/COLOR]
    Identifier     "Synaptics Touchpad" [COLOR="Red"]Added this line[/COLOR]
    Driver         "synaptics" [COLOR="Red"]Added this line[/COLOR]
    Option         "SendCoreEvents" "true" [COLOR="Red"]Added this line[/COLOR]
    Option         "Device" "/dev/psaux" [COLOR="Red"]Added this line[/COLOR]
    Option         "Protocol" "auto-dev" [COLOR="Red"]Added this line[/COLOR]
    Option         "HorizScrollDelta" "0" [COLOR="Red"]Added this line[/COLOR]
    Option         "SHMConfig" "on" [COLOR="Red"]Added this line[/COLOR]
EndSection [COLOR="Red"]Added this line[/COLOR]

I've come across some posts that state "SHMConfig" should be set to "true" . That didn't work for me. Setting it to "on" did the trick. Now when I start the touchpad interface (located through /System/Preferences on the menu bar) I don't get an error message.

I hope this helps some of the Ubuntu faithful out there.

---

