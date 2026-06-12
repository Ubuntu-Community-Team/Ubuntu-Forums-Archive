---
title: "Middle Mouse Scroll Wheel"
date: 2010-06-04
forum: Hardware
---

### Post by Vock on 2010-06-04
I've noticed that the default wheel scroll up/down in ubuntu does nothing, but if you were to hold down the alt key, it acts as a scroll wheel, allowing you to scroll up and down within the current active window.

I was wondering if there was a way to make this possible without having to push down the alt key? 

Most posts I've read deal with clicking the middle mouse button and having it scroll with the position of the mouse, which isn't what I'm looking for.


Thanks,
Vick

Edit: The mouse wheel does scroll up, but it doesn't scroll down. This seems weird to me.

---

### Post by luceerose on 2010-06-04
Try replacing the mouse section of your xorg file with something a little more versatile.

To edit xorg file open a terminal &;
```
gksu gedit /etc/X11/xorg.conf
```

Replace the whole mouse section with something like this;
```
Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "vmmouse" 
Option "CorePointer" 
Option "Device" "/dev/input/mice" 
Option "Protocol" "ExplorerPS/2" 
Option "ButtonMapping" "1 2 3" 
Option "ZAxisMapping" "4 5" 
Option "YAxisMapping" "6 7" 
Option "Emulate3Buttons" "no" 
Option "Resolution" "800" 
EndSection
```

---

### Post by Vock on 2010-06-08
Tried that, unfortunately it still doesn't work :( 

Any other ideas?

---

### Post by Vock on 2010-06-25
I found out that it's the default settings in Compiz for the Rotate Cube plugin that are throwing it off. With Desktop Wall, there's no problems with the middle mouse scroll wheel. I just disabled the Initiate binding for Rotate Cube, and my scroll wheel works, and I can still rotate if i hold down the middle mouse button. Hope that helps whoever else is suffering from this.

---

### Post by usndmac on 2010-07-06
I have an upgraded 9.04 -> 10.04 with ps2 mouse and Compiz is not activated.

The scroll wheel scrolled as the default action in 9.04, it no longer scrolls in 10.04.

I've read the man pages for xorg.conf, but, is there any tutorial documentation on the whole xorg.conf thing?

---

