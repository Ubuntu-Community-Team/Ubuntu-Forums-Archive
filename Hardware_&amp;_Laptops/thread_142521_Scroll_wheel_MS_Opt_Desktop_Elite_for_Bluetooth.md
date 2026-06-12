---
title: "Scroll wheel: MS Opt Desktop Elite for Bluetooth"
date: 2006-03-10
forum: Hardware &amp; Laptops
---

### Post by johan_lunds on 2006-03-10
Okey, I've seen different threads on the subject, but I just can't get it working.
I've got "MS Keyboard Elite for Bluetooth" and "MS IntelliMouse Explorer for Bluetooth". They connect with bluez-utils and HID --search or whatever it was. That works fine. First of all I want my scroll wheel (incl. side-scrolling) to work, and after that the thumb buttons. I'd like the scroll wheel on the keyboard to work as well. I've read some different threads on this but nothing has worked.

In xev only mouse button 1, 2 and scroll wheel clicking works (button 3).

my xorg.conf
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
 	 Identifier	"Configured Mouse"
 	 Driver		"mouse"
 	 Option		"CorePointer"
	 Option		"Device" 			 "/dev/input/mice"
	 Option		"Protocol"			 "ExplorerPS/2"
	 Option	 	"Buttons" 			 "9"
 	 Option	   	"ZAxisMapping"			 " 6 7"
EndSection
```

I've tried different settings for ZAxisMapping and Buttons. I've tried imwheel but uninstalled and erased those files.

Can anyone help me? I really need that scroll wheel :P it really speeds things up.

My product: [http://www.microsoft.com/PRODUCTS/info/product.aspx?view=22&pcid=76e91501-ff1c-44cf-947f-003f3fe25a8c&type=ovr](http://www.microsoft.com/PRODUCTS/info/product.aspx?view=22&pcid=76e91501-ff1c-44cf-947f-003f3fe25a8c&type=ovr) though it's not coloured like that. Maybe this can be to any help:
[LIST]
[*]WUT0456 (it's a zero, not the letter O)
[*]MS PART NO. X800122-112
[/LIST]

Appreciate any help, thx!
/Johan Lundström, Sweden
johan_ lunds hotmail .com

---

### Post by stfu on 2006-03-20
Does the mouse have 9 buttons? Try this, might get the scroll-wheel to work.

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ZAxisMapping" "4 5"
EndSection

For the keyboard wheel, see what system>settings>keyboard has to offer. Mine works when I select a keyboard with similiar layout (MX900 - Logitech Internet Navigator Keyboard).

---

