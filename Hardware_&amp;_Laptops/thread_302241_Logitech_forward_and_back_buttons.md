---
title: "Logitech forward and back buttons"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by Scotch on 2006-11-18
Is it possible to get the for and backward buttons on my logitech mouse to work?

Scotch

---

### Post by donmarone on 2006-11-18
Yes, it is. Just use the "evdev" driver for the mouse.

Don Marone

---

### Post by Scotch on 2006-11-18
Where do I find this ''evdev'' thing? You see, I'm new here :-k 

Scotch

---

### Post by GenX on 2006-11-19
I am having the same issue on my trackball logitech. I don't understand anything about drivers at this point in the game either.

---

### Post by bilange on 2006-11-19
Well, I didn't need to use any special "drivers" to have my forward/back buttons working on my Logitech MX500. 

Heres the Mouse section of my /etc/X11/xorg.conf - the interesting part is the "Buttons" and "ButtonMapping" lines.

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
[B]        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"[/B]
EndSection

```

If I am not mistaken, xorg can only handle 5 buttons at once... thats what ive read on the net (I lost the source, though).

How to use this info: in a console, type in sudo **gedit /etc/X11/xorg.conf** and look for a section where Mouse is specified. Once found, add the lines I marked in bold, and either reboot or restart X (typing Ctrl+Alt+Backspace should do the trick. If you use Ctrl+Alt+Backspace, save your data, all programs will close!), and try the back/forward buttons in firefox or whatever.

If you are quite new about editing this file, be very careful, as modifying something that you shouldnt can make your X Server (graphical interface) not startable anymore!

---

### Post by Scotch on 2006-11-20
> **bilange said:**
> Well, I didn't need to use any special "drivers" to have my forward/back buttons working on my Logitech MX500. 

Heres the Mouse section of my /etc/X11/xorg.conf - the interesting part is the "Buttons" and "ButtonMapping" lines.

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
[B]        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"[/B]
EndSection

```

If I am not mistaken, xorg can only handle 5 buttons at once... thats what ive read on the net (I lost the source, though).

How to use this info: in a console, type in sudo **gedit /etc/X11/xorg.conf** and look for a section where Mouse is specified. Once found, add the lines I marked in bold, and either reboot or restart X (typing Ctrl+Alt+Backspace should do the trick. If you use Ctrl+Alt+Backspace, save your data, all programs will close!), and try the back/forward buttons in firefox or whatever.

If you are quite new about editing this file, be very careful, as modifying something that you shouldnt can make your X Server (graphical interface) not startable anymore!


My computer got ****** up:-k 

Now I have 2 start all over again](*,)

---

### Post by John.Michael.Kane on 2006-11-21
This may help [HOWTO: Configuring Logitech mice in Ubuntu ]("http://www.ubuntuforums.org/showthread.php?t=219894&highlight=Logitech+lx7")

---

### Post by nfriedly on 2006-11-27
> **bilange said:**
> Well, I didn't need to use any special "drivers" to have my forward/back buttons working on my Logitech MX500. 

Heres the Mouse section of my /etc/X11/xorg.conf - the interesting part is the "Buttons" and "ButtonMapping" lines.

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
[B]        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"[/B]
EndSection
```

If I am not mistaken, xorg can only handle 5 buttons at once... thats what ive read on the net (I lost the source, though).

How to use this info: in a console, type in sudo **gedit /etc/X11/xorg.conf** and look for a section where Mouse is specified. Once found, add the lines I marked in bold, and either reboot or restart X (typing Ctrl+Alt+Backspace should do the trick. If you use Ctrl+Alt+Backspace, save your data, all programs will close!), and try the back/forward buttons in firefox or whatever.

If you are quite new about editing this file, be very careful, as modifying something that you shouldnt can make your X Server (graphical interface) not startable anymore!

This worked perfectly for me. Thank you!

I have a logitech MX 1000 and my /etc/x11/xorg.conf now reads:

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection
```

I find it interesting that it was able to automatically detect my battery's percentage, but couldn't set up forward and back buttons on it's own. Maybe something for the next release...

---

### Post by smellydog on 2007-02-24
Well, i have a Logitech Lx7 and it sort of worked for me.  I have my page back and page forward working just fine, but my tilt wheel only goes one way.  Never had a tilt wheel mouse before so i suppose i can live with it for now.  But all i did was edit my xorg.conf and added the two lines for the buttons and buttonmapping.  It is an improvement from where i was at!

---

