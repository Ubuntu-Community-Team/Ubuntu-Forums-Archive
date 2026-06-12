---
title: "Logitech g9"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by manatawady on 2007-11-23
Anyone got it working completely, including the wheels left/right buttons?

---

### Post by manatawady on 2007-11-29
Since noone replied that had a working config Ill try to add details to my mouse:
Its a 9 button mouse - mouse left/right, wheel pressed, forward backwards wheel left/right and 2 thumb buttons (who would have thought -actually is a bit like the g5 which has 2 thumb buttons too i believe and that tilt wheel).
My config so far recognizes all buttons except the wheel tilted to left is like mouse4 and wheel tilt to the right aint recognized at all.
```
cat /proc/bus/input/devices:

: Bus=0003 Vendor=046d Product=c048 Version=0111
N: Name="Logitech G9 Laser Mouse"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/class/input/input3
U: Uniq=D43A11CD730029
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c048 Version=0111
N: Name="Logitech G9 Laser Mouse"
P: Phys=usb-0000:00:02.0-3/input1
S: Sysfs=/class/input/input4
U: Uniq=D43A11CD730029
H: Handlers=kbd event4 
B: EV=10000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8837c007 ffe67bfa d9415fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0

```

So the mouse has two different handlers: mouse1 event3 and kbd event4 

Anyone has an idea how to combine those two events that the mouse requires?
Does the mouse really require those two different handlers to make use of all the buttons?

---

### Post by DancingCat on 2007-12-20
Yes I have a Logitech g9 as of about 2 hours ago.

I have all the buttons reporting events in xev and they all detect in Quake Wars Enemy Teritority.

That is.
Left Mouse                  Button 1
Middle Mouse             Button 2
Right Mouse                Button 3
Scroll wheel up           Button 4
Scroll wheel Down     Button 5
Wheel Tilt Right          Button 6
Wheel Tilt Left            Button 7
Thumb Forward          Button 8
Thumb Back                Button 9


My xorg.conf is as follows...

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         **"evdev"**
    Option		   "Name" 					**"Logitech G9 Laser Mouse"**
    Option		   "Vendor"					**"046d"**
    Option		   "Product"				**"c048"**
    Option         "Protocol" 				"auto"
    Option         "Device" 				**"/dev/input/event4"**
    Option         "Emulate3Buttons" "no"
    Option         "Buttons"               "9"
    Option         "ZAxisMapping"          "4 5"
    Option         "ButtonMapping"         "1 2 3 6 7 8 9"
    Option         "Resolution"            "2000"
EndSection


You have to run cat /proc/bus/input/devices to get the right information to fill in the bold fields. heres the output from mine yours WILL be different ( probably ).

I: Bus=0003 **Vendor=046d Product=c048** Version=0111
N: Name=**"Logitech G9 Laser Mouse"**
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/class/input/input9
H: Handlers=mouse1 ts1 **event4 **
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c048 Version=0111
N: Name="Logitech G9 Laser Mouse"
P: Phys=usb-0000:00:13.0-2/input1
S: Sysfs=/class/input/input10
H: Handlers=kbd event5 
B: EV=10000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8807c007 ffe67bfa d9415fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0

There are two section, I have no idea why the mouse also registeres with the keyboard handler but ignore the second section.

I hope this helps someone and happy mousing....

Now for some serious head shots :)

Liquidity.

---

### Post by keyboardslave on 2007-12-23
Greetings,

I recently got a new g15 (new type).
and a g9 mouse. from my missus as a early chrissy present lol.

i got both working 100% with these 2 tutorials. i even have the colors on my laser mouse change.

mouse, <http://morecode.wordpress.com/2007/11/22/logitech-g9-on-linux/>

keyboard, <http://ubuntuforums.org/showpost.php?p=2461304&postcount=285>

:twisted:

Kind regards,

---

### Post by manatawady on 2007-12-24
inclusive the mouse tilt wheel?:guitar:
@keyboardslave does your xorg.conf enty look similar to it ?
Did u copy paste this one or modify anything to suit ubuntu

And which version of ubuntu are u running?

Thanks for your answer btw :)

---

### Post by manatawady on 2007-12-25
Suppose I should try before asking :)
It works so far with the side buttons activated - like for scrolling back and forw in ff.
Tilt wheel doesnt work so far - but ill  try to bind keys to it

---

### Post by keyboardslave on 2008-01-02
srry for the late response mate,

i have the extra buttons working on world of padman though the tilt is not, though i havnt tried to get it to work. 
im using ubuntu feisty 7.04 i really should upgrade :P

I didnt change anything in my xorg.conf but ill post it for u anyway :)

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


but hey it still works

---

### Post by zear on 2008-02-25
Hi, 
and thanks for this page, my G9 works now.

I think there's no HWheel on this mouse, pressing the wheel to the left is the same as clicking it(b2). It's not clickable to the right...

+

---

### Post by mac.ryan on 2008-03-29
I have a g9 since a few hours... Changing the xorg.conf (for some mysterious reason) cause troubles with my graphic card (Geforce 7900 gtx)... What I did to work around the issue:[LIST=1]
[*]go on a machine with window$ and install the setpoint application (the mouse configurator)
[*]assign all the button to an ascii character (assign keystroke option from the configurator menu) - i advice choosing composite chars (those normally obtained with AltGr like &#322;, ¶, &#359;, &#8592;, &#8595;, etc..) so not to "take away" the possibility to use all the keys on the keyboard for other purposes.
[*]save the configuration on the mouse memory
[*]bring my mouse back to my machine
[*]select the profile with the button on the bottom of the mouse
[*]enjoy the various games[/LIST][B]...and yes... this mouse has both left and right tilt wheel and they both work in ubuntu following the procedure above.
[/B]
So, my answer to the original post is: yes, I managed to make it work completely, including the tilt wheel! :)

---

