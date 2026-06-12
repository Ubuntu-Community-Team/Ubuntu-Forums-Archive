---
title: "Mouse moves, but then goes back to middle"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by crxgames on 2005-07-30
I have just done a fresh install of ubuntu and all seems to be fine but my mouse. Starting at login, the mouse will move, but then move back to a location some where by where you moved the mouse from in the first place. I have done a dist-upgrade and that didn't fix anything. I am completely lost on what to do here, as I have never had this happen on any other version of linux, so any help would be appreciated. :)

---

### Post by crxgames on 2005-08-03
[QUOTE=crxgames]I have just done a fresh install of ubuntu and all seems to be fine but my mouse. Starting at login, the mouse will move, but then move back to a location some where by where you moved the mouse from in the first place. I have done a dist-upgrade and that didn't fix anything. I am completely lost on what to do here, as I have never had this happen on any other version of linux, so any help would be appreciated. :)[/QUOTE]
 Here is the mouse section from xorg.conf

```

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "Auto"
Option "Emulate3Buttons" "true"
Options "ZAxisMapping" "4 5"
EndSection

```

Here is my working section from SuSE linux, but doesn't effect anything on ubuntu:

```

Section "InputDevice"
Driver "mouse"
Identifier "Mouse[1]"
Option "Buttons" "7"
Option "Device" "/dev/input/mice"
Option "Name" "ImExPS/2 Logitech Explorer Mouse"
Option "Protocol" "explorerps/2"
Option "Vendor" "Sysp"
Option "ZAxisMapping" "4 5"
EndSection

```

I have also tried using /dev/psaux with no luck. :(

---

### Post by wrtrdood on 2005-08-03
The last time I had a problem similar to this it was because I had two devices configured.  Seems like it was related to having them both configured as CorePointer in the ServerLayout section of the X config file.  For Xorg that would be xorg.conf.

Just a thought.

---

