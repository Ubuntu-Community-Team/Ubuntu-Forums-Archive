---
title: "mouse pointer moves on it's own!"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by pete0r on 2005-05-27
whenever i try to click on something, my mouse pointer moves a bit to the left all on it's own. i thought maybe it's the surface i'm using, but i've tried serveral and i have the same problem with all of them.

i'm using the config from this thread: [http://www.ubuntuforums.org/showthread.php?t=27833&highlight=mx700](http://www.ubuntuforums.org/showthread.php?t=27833&highlight=mx700)

which is
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Buttons" "9"
EndSection

any ideas? i'm using a logitech mx700.

thanks!

---

### Post by ltmon on 2005-05-27
I think some optical mouses are just like that.  Mine at work does it on a win2k machine... it's pretty annoying!

---

### Post by pete0r on 2005-05-28
[QUOTE=ltmon]I think some optical mouses are just like that.  Mine at work does it on a win2k machine... it's pretty annoying![/QUOTE]
 well it never did that in windows. oh well

---

