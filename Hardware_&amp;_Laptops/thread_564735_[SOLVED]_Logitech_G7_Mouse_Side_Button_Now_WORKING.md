---
title: "[SOLVED] Logitech G7 Mouse Side Button Now WORKING"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by measekite on 2007-10-01
I have posted quite a bit for help on getting the Logitech G7 Side Button to Work.  While I have followed all of the posted instructions (using the evedv driver) and numerous edits of Xorg it failed to work.

I finally succeeded in making the buttons to work.  The method is short, simple and sweet.

[B][COLOR=Red]Here are the instructions:

[/COLOR][/B][COLOR=Red][COLOR=Black]Edit the file /etc/X11/xorg.conf

[/COLOR][/COLOR]```
gksudo gedit
```Open [COLOR=Red][COLOR=Black]/etc/X11/xorg.conf
Change: 
Section "InputDevice"
         Identifier "Configured Mouse"
         Driver "mouse"
         Option "CorePointer"
         ...
         Option "Protocol" "ExplorerPS/2"
         ...
         Option "Emulate3Buttons"       "true"
EndSection

to: 

[/COLOR][/COLOR]```
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "ZAxisMapping" "4 5"
        Option "Emulate3Buttons" "true"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
EndSection
```[COLOR=Red][COLOR=Black] Here are the button functions:

Button 1 Left Click
Button 3 Right Click
Button 2 Scroll Wheel Click (up/down)
Button 4 Scroll Wheel Forward
Button 5 Scroll Wheel Back
Button 6 Side Button

Horizontal scrolling (Scroll Wheel Left and Right still do not work.  If anyone knows how to get this working please post.

[B]Buttons still won't work in Nautilus unless you install the imwheel dameon. 

[COLOR=Red]I will file another post when I get this working.[/COLOR]
[/B]    


[/COLOR][/COLOR]

---

