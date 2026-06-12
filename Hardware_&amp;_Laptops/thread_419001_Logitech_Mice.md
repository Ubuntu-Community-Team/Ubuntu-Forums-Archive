---
title: "Logitech Mice"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by itchanddino on 2007-04-22
In Dapper and Edgy, all I had to do to get my side buttons working in Firefox was follow this : [URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#Mice"]http://ubuntuguide.org/wiki/Ubuntu:Feisty#Mice
[/URL]
however, now when I try the same method it doesn't work.  Is there a way to do this without installing extra software?  If not, should I just use IMWheel?  Thanks!

---

### Post by kerry_s on 2007-04-22
It works in mine, did you restart x? (reboot or ctrl+alt+backspace)

---

### Post by itchanddino on 2007-04-23
yeap, I even restarted

---

### Post by Unbound Spectre on 2007-04-23
I am not sure if this will help, but this is what I use in Edgy with my MX518.

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 2 3 6 7 4 5"
EndSection
```

---

### Post by itchanddino on 2007-04-23
It seems to be that it defaults to IMPS/2 instead of ExplorerPS/2. weird.

---

