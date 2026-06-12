---
title: "Logitech LX700 Keyboard Hotkeys"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by survient on 2007-03-31
Ok, I have a logitech LX700 keyboard, however I don't think ubuntu is recognizing my media keys properly. I ran the Hotkeys applet and tried to map the keys as I wanted, but it maps my play/pause button and my previous track button to the same key. The same goes for my stop button and my forward track button. Is there any way to customize it manually?

---

### Post by gjtoth on 2007-03-31
> **survient said:**
> Ok, I have a logitech LX700 keyboard, however I don't think ubuntu is recognizing my media keys properly. I ran the Hotkeys applet and tried to map the keys as I wanted, but it maps my play/pause button and my previous track button to the same key. The same goes for my stop button and my forward track button. Is there any way to customize it manually?

I have the LX710.  I just used the keyboard shortcuts options and mine works fine.  I also have the fix for getting the multi-button mouse to work.

---

### Post by survient on 2007-03-31
I'd like to know the fix for the mouse, however the keyboard shortcuts is the app I'm having trouble with, it's mapping some of my keys to the same values, and I don't understand why.

---

### Post by gjtoth on 2007-04-01
> **survient said:**
> I'd like to know the fix for the mouse, however the keyboard shortcuts is the app I'm having trouble with, it's mapping some of my keys to the same values, and I don't understand why.

In a console type:

sudo nano /etc/X11/xorg.conf

replace the mouse section with:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons" "false"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

---

### Post by wampirek on 2007-04-06
> **gjtoth said:**
> In a console type:

sudo nano /etc/X11/xorg.conf

replace the mouse section with:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons" "false"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

It works great with 2 tiny buttons, but I can't see any effects when I push mouse wheel to the sides (you know - left and right). 
Besides - is there any way to connect some actions to the buttons on the left side of keyboard? Hotkeys applet seems not to be able to see them... 

BTW - do you have the same problem as described here: [http://tinyurl.com/32eyjt](http://tinyurl.com/32eyjt)

---

